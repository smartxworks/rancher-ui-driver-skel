# Rancher UI Driver of SMTX OS

Rancher UI driver for the [docker-machine-driver-smtxos](https://github.com/smartxworks/docker-machine-driver-smtxos)

## Setup

* Add SMTX OS Node Driver in Rancher 2.x (Global -> Tools -> Drivers -> Node Drivers -> Add Node Driver)
  * Download URL: `https://github.com/smartxworks/docker-machine-driver-smtxos/releases/download/v0.1.0/docker-machine-driver-smtxos-0.1.0.linux-amd64.tar.gz`
  * Custom UI URL: `https://smartxworks.github.io/rancher-ui-driver-smtxos/releases/v0.1.x/component.js`
  * Whitelist Domains: `smartxworks.github.io`
* Wait for the driver to become "Active"
* Go to Global -> Clusters -> Add Cluster, SMTX OS driver should show up.

## Development

This package contains a small web-server that will serve up the custom driver UI at `http://localhost:3000/component.js`.  You can run this while developing and point the Rancher settings there.

* `npm start`
* The driver name can be optionally overridden: `npm start -- --name=smtxos`
* The compiled files are viewable at http://localhost:3000.
* **Note:** The development server does not currently automatically restart when files are changed.
* Do not use the `model.smtxosConfg` signature to access your driver config in the template file, use the `config` alias that is already setup in the component

## Building

For other users to see your driver, you need to build it and host the output on a server accessible from their browsers.

* `npm run build`
* Copy the contents of the `dist` directory onto a webserver.
  * If your Rancher is configured to use HA or SSL, the server must also be available via HTTPS.
