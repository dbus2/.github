# The future of D-Bus happens here

## Introduction

[D-Bus] is a message bus system, a simple way for applications to talk to one another. In addition 
to interprocess communication, D-Bus helps coordinate process lifecycle; it makes it simple and
reliable to code a "single instance" application or daemon, and to launch applications and daemons
on demand when their services are needed.

The goal of this umbrella project is to provide safe and modern D-Bus implemententations, using the
Rust programming language. This initiative is split into two main projects:

* [`zbus`]: A pure Rust D-Bus library, that focuses on ease of use. `zbus` is already a
  well-established library, and is used in production by several projects and companies.

* [`busd`]: A D-Bus daemon/broker, that aims to be a drop-in replacement for the reference
  implementation of D-Bus, `dbus-daemon` and [`dbus-broker`]. `busd` is not yet ready for
  production use.

[D-Bus]: https://www.freedesktop.org/wiki/Software/dbus/
[`zbus`]: https://github.com/dbus2/zbus
[`busd`]: https://github.com/dbus2/busd
[`dbus-broker`]: https://github.com/bus1/dbus-broker
