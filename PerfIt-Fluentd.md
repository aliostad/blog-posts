fluentd support in PerfIt
==

After a few years of several contending products and tools in the *tracing middleware*, it seems that the industry has settled on [fluentd](https://docs.fluentd.org). I believe this is probably because it has maintained technology-neutrality when it comes to ultimate destination of metrics and logs, i.e. storage/visualisation/search/alerting aspect.

The journey had started with Etsy's [statsd](https://github.com/statsd/statsd/wiki) back in 2012. It allowed for collection of metrics mainly using UDP which started an important if not revolutionary trend. On the other hand, [Zipkin](https://zipkin.io/) project came out of internal works in Twitter inspired by Google's [Dapper paper](https://ai.google/research/pubs/pub36356). 

Zipkin had poised to become the universal Open Source distributed tracing solution. It certainly inspired the OpenTracing initiative but the more OpenTracing grew, the more it dented the status of Zipkin, as OpenTracing improved on some of the shortcomings of Zipkin that were kept in order to maintain backward compatibility. I actually worked with Zipkin community and its amazing community leader, Adrian Cole, to bring Zipkin support to Azure Event Hubs. I also started adding support for Zipkin to the PerfIt project (I did not get a chance to use it in anger and I doubt anyone else used it). Regardless of its merits, drawbacks and its future, it couples middleware with storage and search and is not a pure middleware. 

Another contender was LogStash which then morphed into [Beats](https://www.elastic.co/products/beats) and was the default choice for collection of metrics and logs in Elasticsearch. But then again, these technologies are optimised for use with Elasticsearch and Kibana. 

## fluentd is ubiquitous
Now, with fluentd being a default choice with Kubernetes, it understandably has gained wide adoption. Having said that, I believe it says more about fluentd than Kubernetes as there is so much to love about fluentd since it:

 - Is simple and straightforward 
 - Is Open Source
 - Supports many inputs/transports (HTTP, UDP, file)
 - Supports common output types (Elasticsearch, s3, kafka)
 - Supports many formats/parsers (csv, json, nginx)
 - Supports transformations and buffering
 - Does not try to solve high availability and instead provides probes so that infrastructure can monitor
 - Provides extension points using the plugin model

That is why I believe it will be a glue that will be binding producers and consumers of observability data for the coming years. And that is the main reason I felt I had to support it in PerfIt.

## PefIt and fluentd
For those of you who are not familiar with PerfIt, I started the project more than 6 years ago for instrumenting .NET systems - in the absence of similar tool. Initially it was meant only for custom Windows performance counters but gradually grew to support ETW and finally with .NET Core to support other forms of transport such as Azure Event Hubs.

Now I support fluentd using UDP transport.

## Getting started
I have blogged in the past on using PerfIt but essentially you create an instrumentor and instrument a piece of code:

``` csharp
var si = new SimpleInstrumentor(new InstrumentationInfo()
{
    Description = "Instruments your code!",
    Name = "general",
    CategoryName = "my app",
    InstanceName = "Sleep100"
});

si.Instrument(() =>
{
    Thread.Sleep(100);
});

```

You can also achieve this using AOP with attributes in ASP.NET Web Api or Core MVC. 

You can register tracers which are essentially outputs/sinks for your captured metrics. Currently Azure EventHubs, Zipkin and fluend are supported - the latter is the new addition:

``` csharp
// add the tracer after creating instrumentor - sends UDP datagrams to localhost on port 5160
si.Tracers["fluentd"] = new UdpFluentdTracer("localhost", 5160);
```

That is really it! This means all your *sampled* traces will be sent to your fluentd. Easy peasy...