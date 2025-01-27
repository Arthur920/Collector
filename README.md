# OpenTelemetry Collector 

This is an adaptation of the Demo Collector provided in the [OpenTelemetry Collector Contrib Repository](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main)

This demo contains a client and server applications that use the 
opentelemetry Go library for instrumentation and for sending telemetry data
to the opentelemetry collector.

The client periodically makes http calls to the server which
create client spans, server spans and metrics that track information like
number of http requests and latency.

This demo presents the typical flow of observability data with multiple
OpenTelemetry Collectors deployed:

- The client and server send data directly to the OTel Collector;
- The OTel Collector then sends the data to the appropriate backend, in this demo
Jaeger, Zipkin, and Prometheus -> Grafana backend will be added by me sooner or later

This demo uses `docker-compose` and by default runs against the
`otel/opentelemetry-collector-contrib:0.177.0` image. (changed to newest version) 

To run the demo switch to the root directory of the repository and run:

```shell
docker compose up -d
```

The demo exposes the following backends:

- Jaeger at http://0.0.0.0:16686
- Zipkin at http://0.0.0.0:9411
- Prometheus at http://0.0.0.0:9090
- Grafana at http://0.0.0.0:3000

Notes:

- username & password credentials are unless changed by default both 'admin' 

- The demo uses the otel-collector-config.yaml for different configurations adjust the docker-compose.yaml accordingly.

- It may take some time for the application metrics to appear on the Prometheus
 dashboard;

To clean up any docker container from the demo run `docker-compose down`.