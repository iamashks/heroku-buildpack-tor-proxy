# Tor Proxy Buildpack for Heroku

This buildpack sets up [Tor Proxy][1] for your app on Heroku.

> Tor is a program you can run on your computer that helps keep you safe on the Internet. It protects you by bouncing your communications around a distributed network of relays run by volunteers all around the world: it prevents somebody watching your Internet connection from learning what sites you visit, and it prevents the sites you visit from learning your physical location. This set of volunteer relays is called the Tor network.

## Setup

With this buildpack installed, Tor Proxy runs automatically on the port: 9050.

**NOTE:** Tor Proxy is a SOCKS-proxy and only works with SOCKS-supporting apps.

#### Create a new app with this buildpack

Create a new Heroku app with this buildpack (through the [Heroku CLI][2]):

```shell
heroku create --buildpack "https://github.com/iamashks/heroku-buildpack-tor-proxy.git"
```

#### Or, add this buildpack to an existing app

1] Create a Heroku app as normal with the usual buildpacks.

2] Then, add this buildpack in your app (through the [Heroku CLI][2]):

```shell
$ heroku buildpacks:add https://github.com/iamashks/heroku-buildpack-tor-proxy.git
```

## Variables

You'll need to provide these as env variables ([check this guide][3]):

* `TOR_VERSION`: The version of Tor to install (default: its latest version).
* `TOR_PROXY_PORT`: The port to be used for the proxy server (default: 9050).
* `TOR_CONTROL_PORT`: The port to be used for the control server (default: 9051).
* `TOR_CONTROL_PASS`: The password for the control server (default: "torProxy@123").
* `TOR_CONF_FILE_URL`: The configuration for Tor to follow (default: Tor's default `torrc`).

**NOTE:** `TOR_PROXY_PORT`, `TOR_CONTROL_PORT`, and `TOR_CONTROL_PASS` override any values 
you provide in the custom `torrc` file defined by the `TOR_CONF_FILE_URL`. If you need to 
provide the values for these three variables, provide them through env variables rather than 
your custom `torrc`. 

## Features

* Caches compilation
* Verifies integrity (confirm yourself; it's provided as is without any warranty)

[1]: https://www.torproject.org/
[2]: https://devcenter.heroku.com/articles/heroku-cli#getting-started
[3]: https://devcenter.heroku.com/articles/config-vars#using-the-heroku-dashboard
