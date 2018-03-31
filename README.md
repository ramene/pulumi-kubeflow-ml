# Pulumi Examples

This repository contains examples of using Pulumi to build and deploy cloud applications and infrastructure.

Each example has a two-part prefix, `<cloud>-<language>`, to indicate which `<cloud>` and `<language>` it pertains to.
The cloud is one of `aws` (for [Amazon Web Services](https://github.com/pulumi/pulumi-aws)), `azure` (for [Microsoft
Azure](https://github.com/pulumi/pulumi-azure)), `gcp` (for [Google Cloud
Platform](https://github.com/pulumi/pulumi-gcp)), `kubernetes` (for
[Kubernetes](https://github.com/pulumi/pulumi-kubernetes))), or `cloud` (for
[Pulumi's cross-cloud programming framework](https://github.com/pulumi/pulumi-cloud)).

See the [Pulumi documentation](https://docs.pulumi.com) for more details on getting started with Pulumi.

### Web Server

This is one of our most basic examples, showing how to provision a simple Linux webserver serving traffic on port 80.
This example is available in multiple flavors:

* [AWS EC2 instance in JavaScript](aws-js-webserver)
* [AWS EC2 instance in Python](aws-py-webserver)
* [Azure Virtual Machine in JavaScript](azure-js-webserver)
* [Kubernetes Nginx in TypeScript](kubernetes-ts-webserver)

An [extension of this example](aws-js-webserver-component/) demonstrates creating a minimal component that encapsulates
creating EC2 instances, highlighting one of the benefits of using general purpose languages for managing infrastructure.

### [Cloud-Agnostic URL Shortener](cloud-ts-url-shortener/)

This example demonstrates a complete URL shortener web application using high-level `cloud.Table` and
`cloud.HttpEndpoint` components, highlighting the ability to combine deployment time and runtime code, and the simple,
cloud-agnostic, programming model of `@pulumi/cloud`.  Although we only support AWS today in this framework, our plan
is to offer an implementation of this on all major clouds, and so any code targeting this can truly run anywhere.

An [extension of this example](url-shortener-with-cache/) adds a reusable cache component to the URL shortener
using `cloud.Service` to run a containerized Redis image.  This shows that you can create your own `cloud.*`-like
abstractions for your own use, your team's, or to share with the community using your language's package manager.

## [AWS Video Thumbnailer](aws-js-video-thumbnailer/)

This example features an end-to-end pipeline for generating keyframe thumbnails from videos uploaded to a bucket using
containerized [FFmpeg](https://www.ffmpeg.org/).  It combines containers, serverless functions, and cloud storage into
a single 40-line application using `@pulumi/cloud-aws`.

### [Raw AWS Serverless](aws-js-serverless-raw/)

This example deploys a complete serverless C# application using raw `aws.apigateway.RestAPI`, `aws.lambda.Function` and
`aws.dynamodb.Table` resources from `@pulumi/aws`.  Although this doesn't feature any of the higher-level abstractions
from the `@pulumi/cloud` package, it demonstrates that you can program the raw resources directly available in AWS
to accomplish all of the same things this higher-level package offers.

The deployed Lambda function is a simple C# application, highlighting the ability to manage existing application code
in a Pulumi application, even if your Pulumi code is written in a different language like JavaScript or Python.
