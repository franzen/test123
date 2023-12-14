# Wittra Documentation

> **Note:** This page is not visible in the user documentation.

This repository contains the user-targeted documentation for the Wittra product.

## Running Locally

The documentation is built using [Docsify](https://docsify.js.org/) and is hosted via [GitHub Pages](https://github.com/wittra/docs.wittra.se/settings/pages).

To run the documentation site locally, follow these steps:

1. Install Docsify:
    ```console
    $ npm i docsify-cli -g
    ```

2. Serve the documentation:
    ```console
    $ docsify serve docs
    ```
3. This command will serve the documentation at http://localhost:3000 and display the message:
    ```console
    Serving /Path/to/documentation/docs now.
    Listening at http://localhost:3000
    ```

## How to deploy

To deploy a new release, push the changes to the `main` branch of the repository. The updates will be automatically deployed to our production website at [docs.wittra.se](https://docs.wittra.se/).
