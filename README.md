# prom-telemetry-gw

Prometheus Telemetry Gateways is a Prometheus exporter that collects metrics from network devices using streaming telemetry.

## Install
```go get github.com/exaring/openconfig-streaming-telemetry-exporter```

## Run
```
openconfig-streaming-telemetry-exporter -config.file /path/to/config.yml
```

## Configuration


```
listen_address: :8080
metrics_path: /metrics
targets:
- hostname: 169.254.0.0
  port: 50051
  paths:
  - path: /interfaces/
    suppress_unchanged: false
    max_silent_interval_ms: 20000
    sample_frequency_ms: 2000
  - path: /network-instances/network-instance/protocols/protocol/bgp/
    suppress_unchanged: false
    max_silent_interval_ms: 20000
    sample_frequency_ms: 2000
string_value_mapping:
  /interfaces/interface/state/oper-status:
    DOWN: 0
    UP: 1
  /network-instances/network-instance/protocols/protocol/bgp/neighbors/neighbor/state/session-state:
    ACTIVE: 3
    CONNECT: 2
    ESTABLISHED: 6
    IDLE: 1
    OPENCONFIRM: 5
    OPENSENT: 4
```
