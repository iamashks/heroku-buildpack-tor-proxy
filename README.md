# Tor Proxy Buildpack for Heroku

This buildpack sets up a Tor Proxy for your app on Heroku.

## Setup

1] Create a Heroku app as normal with the usual buildpacks.

2] Then, add this buildpack in your app (through the [Heroku CLI][2]):

```bash
$ heroku buildpacks:add https://github.com/iamashks/heroku-buildpack-tor-proxy.git
```

3] With this buildpack installed, Tor Proxy runs automatically on the port: 9050.

**NOTE:** Tor Proxy is a SOCKS-proxy and works with SOCKS-supporting applications.

## Variables

You'll need to provide these as env variables ([check this guide][1]):

* `TOR_VERSION`: The version of Tor to install (default: its latest version).
* `TOR_CONTROL_PORT`: The port to be used for the control server (default: 9051).
* `TOR_CONTROL_PASS`: The password for the control server (default: "torProxy@123").

## Features

* Caches compilation
* Verifies integrity (confirm yourself; it's provided as is without any warranty)

[1]: https://devcenter.heroku.com/articles/config-vars#using-the-heroku-dashboard
[2]: https://devcenter.heroku.com/articles/heroku-cli#getting-started
