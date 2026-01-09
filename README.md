
### Test running with integration for developers


## Development bits

This project has several components:
* **wsd/**
  * The Web Services Daemon - which accepts external connections
* **kit/**
  * The client which lives in its own chroot and renders documents
* **common/**
  * Shared code between these processes
* **browser/**
  * The client side JavaScript component
* **test/**
  * C++ based unit tests
* **cypress_test/**
  * JavaScript based integration tests


### Getting changes into 25.04-mobile

You should still develop against `main`, even if you're working on
mobile-only features. Changes made in `main` will be moved into the
`distro/collabora/co-25.04` branch according to the release schedule. Changes
from the `distro/collabora/co-25.04` branch are then regularly cherry-picked
into the `distro/collabora/co-25.04-mobile` branch.

If you have a change which you want to get into mobile snapshots or releases
more quickly, you should still develop it against `main`. When it's merged
into `main`, you should make a backport pull request against
`distro/collabora/co-25.04-mobile`. Please don't make pull requests directly
against `distro/collabora/co-25.04-mobile` (i.e. without the change first being
merged into `main`).

## Admin Panel

You can access the admin panel by directly accessing the admin.html file
from browser directory.

Websocket connections to admin console can be made at path: /adminws/ on the
same url and port as coolwsd is running on. However, one needs a JWT token to
authenticate to the admin console websocket. This is stored as a cookie with
`Path: /adminws/` when user successfully authenticates when trying to access
/browser/dist/admin/admin\*html files (HTTP Basic authentication). Token
is expired after every half an hour, so websocket connection to admin console
must be established within this period.

It should also be possible to do various sorts of tasks such as killing
documents that are open for more than 10 hours etc. See protocol.txt for
various commands. Only tricky thing here is getting the JWT token which can
be obtained as described above.

## Protocol description

See **[protocol.txt](wsd/protocol.txt)** for a description of the protocol to be used over the
websocket.

## Architecture


## Enjoy!
