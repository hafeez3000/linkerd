# Interfaces

An interface is a published network interface to namerd.

<aside class="notice">
These parameters are available to the interface regardless of kind. Interfaces may also have kind-specific parameters.
</aside>

Key | Default Value | Description
--- | ------------- | -----------
kind | _required_ | Either `io.l5d.thriftNameInterpreter` or `io.l5d.httpController`.
ip | interface dependent | The local IP address on which to serve the namer interface.
port | interface dependent | The port number on which to server the namer interface.

## Thrift Name Interpreter

kind: `io.l5d.thriftNameInterpreter`

A read-only interface providing `NameInterpreter` functionality over the ThriftMux protocol.

Key | Default Value | Description
--- | ------------- | -----------
ip | `0.0.0.0` | The local IP address on which to serve the namer interface.
port | `4100` | The port number on which to server the namer interface.
retryBaseSecs | `600` | Base number of seconds to tell clients to wait before retrying after an error.
retryJitterSecs | `60` | Maximum number of seconds to jitter retry time by.
cache | see [cache](#cache) | Binding and address cache size configuration.
tls | no tls | The namer interface will serve over TLS if this parameter is provided. see [TLS](#namerd-server-tls).

### Cache

Key | Default Value | Description
-------------- | -------------- | --------------
bindingCacheActive | `1000` | The size of the binding active cache.
bindingCacheInactive | `100` | The size of the binding inactive cache.
addrCacheActive | `1000` | The size of the address active cache.
addrCacheInactive | `100` | The size of the address inactive cache.

### namerd server tls

In order to accept incoming tls traffic, the tls parameter must be defined.

Key | Default Value | Description
--- | ------------- | -----------
certPath | _required_ | File path to the TLS certificate file.
keyPath | _required_ | File path to the TLS key file.

## Http Controller

kind: `io.l5d.httpController`

A read-write HTTP interface to the [storage](#storage).

Key | Default Value | Description
--- | ------------- | -----------
ip | loopback | The local IP address on which to serve the namer interface.
port | `4180` | The port number on which to serve the namer interface.
