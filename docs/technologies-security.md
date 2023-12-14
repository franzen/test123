# Security

![img-application](images/applications/applications-medical.png)

We use a Secure-by-design approach where we incorporate security from the
early architecture design stage and throughout the evolution of the products.
The key protections we have are summarized below:

- **Spoofing** is mitigated using an authentication process utilizing JWTs that
  are signed by a private key stored in a TPM on the gateway which are checked in
  registered devices on our cloud service, where the respective public key is
  stored.
- **Tampering** is mitigated using DTLS (6LoWPAN) and Network keys (Mioty)
  to encrypt the data sent between C{x}ameleon devices and the gateway.
  TLS is used between gateway and Wittra portal.
  One caveat is that with the current protocol bridging between the wireless network and HTTP in
  the gateway, **the gateway has to be a trusted device**.
- **Integrity** all firmware images (C{x}ameleon and Gateway) are signed by Wittra and the signatures
  are checked in the device's bootloader. This ensures that the images are approaved and valid Wittra binaries.
- **Confidentiality** is obtained by running CoAP over DTLS (6LoWPAN) and network
  keys (Mioty) from C{x}ameleon to gateway, complemented by HTTPS from gateway to Wittra cloud
  service. The HTTP/TLS link is verified using an X.509 certificate provided by
  the server (in this case Google Cloud Platform) and issued by a trusted
  authority. The DTLS and network keys are verified with a Pre-Shared Key (PSK) which
  is randomly generated at deployment. This key must be kept secret and
  therefore **the gateway has to be treated as a trusted device**.
- **Elevation of Privileges** is handled by standard Linux account
  authentication and authorization mechanisms in the gateway. On our Wittra
  cloud service it is handled by Googles Cloud Identity and Access Management
  (IAM).

## Relevant Pages

* Learn more about the [6LoWPAN](technologies-6lowpan.md) and [Mioty](technologies-mioty.md) networks
* See how to set up [advanced security settings](howto-advanced-gateway-config.md?id=changing-security-settings)