# Tor Hidden Service Buildpack for Heroku

This buildpack sets up a Tor hidden service for your app on Heroku.

## Setup

Create a Heroku app as normal, with any buildpacks you typically use.
If you have a Go app, for instance, deploy it as normal.

Then:

```bash
$ heroku buildpacks:add https://github.com/apg/buildpack-tor-hidden-service.git
```

With the buildpack installed, you'll need to modify your Procfile such that
the hidden service will be setup when the app runs.

```Procfile
web: hide <cmd you'd normally run>
```

## Variables

Of course, Tor hidden services require that you provide a private_key and it's
SHA, for the .onion name. You'll need to provide these as env vars:

* `HIDDEN_PRIVATE_KEY`: The contents of a private_key file
* `HIDDEN_DOT_ONION`: The onion name for the private_key.
