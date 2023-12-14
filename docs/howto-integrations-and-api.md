# Integrations and API

We offer two interfaces for you to interact with your system:
* Integrations: events pushed to you in real-time, as the data arrives;
* REST API: for any interactions such as setting up devices etc.

> **To access sensor data, always prefer integrations over the API**.

Below is a guide to setting up integrations and API calls.
Other relevant pages:
* List of all available endpoints: [API documentation](https://app.swaggerhub.com/apis/wittra-iot/wittra).
* For a description of data formats: [Data Format](resources-data-format.md).

## Integrations
accessing-your-
The Wittra Portal offers two types of integrations for having data pushed to an external system; a general-purpose _Web Hook_ and an integration towards _Cumulocity_.
To set up an integration, go to the project in which your devices are located and click on the _Integrations_ tab.

### WebHook

WebHook integrations require a URL to which data will be sent.
Once a URL has been provided, the Wittra Portal will attempt HTTP POST requests to that URL, with the data payload as the body of the request.
The data is sent as JSON, as denoted by the `Content-Type` header, which is set to `application/json`.

For details on the format of the JSON content, see _Device data_ and _Event data_ below.

For a quick start on how an implementation can be done, there are examples published in this source code [repository](https://github.com/wittra/examples).

> Only the checked device types will have their data propagated to the webhook address.
Data messages for unchecked device types will be discarded.

You can specify a token for the web hook integration. This token is encrypted and stored alongside the integration. Whenever telemetry is sent for any device, if the token is present, we'll pass the **decrypted and base64 encoded** token as a header `auth-token` with the HTTP request.

This can be used to authenticate the request, and the token can be used to verify that the telemetry posted to the webhook URL comes from Wittra. However, it requires an HTTPS connection, since the token could be intercepted and replayed in a non encrypted HTTP session.

### Cumulocity

Integrations with Cumulocity require that you have an account in the Cumulocity platform and a _tenant_ with an associated _tenant domain_ and _tenant ID_.

When the integration has been saved, the devices in your project in the Wittra Portal should appear in the list of devices in the corresponding area in the Cumulocity portal.
Any sensor data that is pushed to the Wittra Portal from a device in your project will be propagated to Cumulocity.

## REST API

To access the REST API, you need an API key. API keys are tied to a specific organization, in contrast to integrations, which are tied to a specific project.
Once an API key has been registered, that API key may be used to access and modify data in all projects in its organization.

Generate an API key by clicking _Manage API Keys_ in the left menu, in an organization in the Wittra Portal.

The base URL for the REST API is `https://api.wittra.se/`.
To authorize, the `Authorization` header is used, where the API key is sent as a password, together with the organization ID as a username.
The values are separated by a colon (`:`) and they are base64-encoded.

See exemple below:
```
Authorization: Basic enU1dk5pQXY5dEpYWm1tSlNGTXY6Zk1YMm9qZ05Ebk0yUkNTbTRYa2RvSXBDZzNXUXRRMDJWV094emFrYjk5WU9TZmJx
```

In the above example, the base64-encoded string corresponds to `zu5vNiAv9tJXZmmJSFMv:fMX2ojgNDnM2RCSm4XkdoIpCg3WQtQ02VWOxzakb99YOSfbq` where `zu5vNiAv9tJXZmmJSFMv` is the ID of the organization and `fMX2ojgNDnM2RCSm4XkdoIpCg3WQtQ02VWOxzakb99YOSfbq` is the API key in use.

The following endpoints are commonly used to access device data:
```
GET /v1/organizations/<organization ID>/projects/<project ID>/devices
GET /v1/organizations/<organization ID>/projects/<project ID>/devices/<device ID>
GET /v1/organizations/<organization ID>/projects/<project ID>/data
```

The REST API can be used not only to retrieve data but also to perform certain actions (e.g. add a device to a project).
