# Thremulation Station
> Cyber Security Operations. For your laptop.

<br>
<p align="center">
<img src="../img/placeholder-logo.png">
</p>
<br>

## What is it?

Thremulation Station is an approachable and ***small-scale threat emulation and detection range*** to emulate and detect adversary activity. Leveraging tools such as VirtualBox and Vagrant Multi-Machine, you can to deploy a _reasonably sized_ local testing environment to _both_ emulate and detect bad things on various guest operating systems.

**There are three basic components:**

1. The Elastic Stack - for analyzing data
2. Atomic Red - for generating adversary activity
3. Victim machines - to be targeted by adversary activity

![](img/ts-workflow.png)

## How is Thremulation-Station different?

Not everyone has a blade server heating their home from a closet...and not everyone, be it a junior hunter/red teamer who is just getting started or an operator with 20 years experience, is an engineer that can stitch all of the complex services together to grow or sharpen your skills.

## Who is it for?

This project has many practical use cases, and we're excited to see how it's used. A few examples:

- Cyber Defense education
- Generating training data
- Threat intelligence training
- Writing and validating [detection rules](https://github.com/elastic/detection-rules)
- Writing and testing threat [tactics and techniques](https://attack.mitre.org/tactics/enterprise/)

## How does it work?

A simple user experience is the priority. A brief usage overview looks like this:

1. Clone the project
1. Use the CLI to deploy your range
1. Reference the User Guide at [thremulation.io](https://thremulation.io)
1. Use the CLI to perform cleanup / reset tasks

> Full details on usage begin in the documentation [Getting Started Guide](getting-started/index.md).

## How can I help?

We welcome contributions! But what if you don't know what to do, or how to start? Check out the [Contribution Section](https://github.com/mocyber/thremulation.io/blob/main/CONTRIBUTING.md). If you're lost, please ask and we can help guide you to the right place to get started.


## Credit

Tools used and projects of inspiration etc.

- Elastic
- Atomic Redpeople
- Mitre Att&ck
- RockNSM
- ...
TODO
