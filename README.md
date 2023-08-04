# D-Bus 2: The future of D-Bus

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

## The plan

### DBus 2 (AKA GVariant)

Apart from providing compatible implementations of the existing [D-Bus protocol], the goal is to
also support D-Bus protocol v2, which in is identical to version 1, but use the [GVariant]
format[^1]. This format is not only more efficient but also solves some of the issues with version
1, for example support for nullable types.

### Additional Header Fields

While the D-Bus spec does not allow custom header fields in messages, `busd` will still support a
few additional on-demand (only) fields, that are useful for certain applications. One example is
addition of [peer credentials] on every message, which can avoid round-trips on the bus.

Once implemented and tested, an effort will be made to add these new fields and related API to the
D-Bus specification.

### Remote Transport

Neither of the current D-Bus implementations support a secure remote transport, which is the reason
many folks choose not to use D-Bus, despite its many great features. Fortunately, the D-Bus
specification is transport-agnostic and hence we will be able to provide a secure remote transport
while maintaining compatibility with the specification.

[D-Bus]: https://www.freedesktop.org/wiki/Software/dbus/
[`zbus`]: https://github.com/dbus2/zbus
[`busd`]: https://github.com/dbus2/busd
[`dbus-broker`]: https://github.com/bus1/dbus-broker
[D-Bus protocol]: https://dbus.freedesktop.org/doc/dbus-specification.html
[GVariant]: https://developer.gnome.org/documentation/specifications/gvariant-specification-1.0.html
[peer credentials]: https://github.com/dbus2/busd/issues/29

[^1]: GVariant was originally planned to be "D-Bus 2" anyway.
