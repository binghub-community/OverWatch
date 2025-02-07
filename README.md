# OverWatch

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

## What is OverWatch?
**OverWatch** is a cloud-based rules creation and enforcement engine designed to incorporate security rules and actions with minimal intervention on your existing applications on AWS whilst accelerating the secure development of your new ones.

## What is the aim of OverWatch?
**OverWatch** aims to provide a low-code, simple and efficient solution to connecting the dots between **AWS CloudWatch** and **security driven application logic**.

**OverWatch** is also designed to be easily installed onto your AWS account as shown below.

## What is a rule?
A rule is a yaml file containing a specific event to look out for, a trigger threshold and an action it may optionally choose to trigger.

This could involve executing an AWS Lambda function which has the power to do virtually anything you want as long as you can integrate it.

## How are rules enforced?
At a glance, **OverWatch** leverages the power of **AWS CloudWatch** and our own integrations to enforce any rules that you have created.

Come to one of our presentations where team 3 goes into a deeper dive into how **OverWatch** works. :)

## What can I define a rule over?
Out of the box, **OverWatch** supports rules to be defined over applications running on AWS deployment instances once the installation process has been completed.

This does not mean that it is limited strictly to AWS deployment instances as long as the application can communicate to **AWS CloudWatch Logs** but the development team does not have the resources to assist in this.

## How does this integrate with my application?
[See video in Quick Start which will show OverWatch in action with an existing project with neglected security practices.](#video-guide-and-demonstration-quick-start)

## Installation
### Video Guide and Demonstration (Quick Start)
[![OverWatch Video Guide and Demonstration](https://img.youtube.com/vi/iumwHlVJtLE/0.jpg)](https://www.youtube.com/watch?v=iumwHlVJtLE)

### OverWatch Core (AWS Deployment)
The easiest way to install the OverWatch Core software into your AWS account is to naviagte on an AWS shell environment to the `ow-pipeline-cdk` folder, then type in the following command:
```
cdk deploy --all
```
Some parameters to modify the CDK deployment are available on [ow-pipeline-cdk readme](ow-pipeline-cdk/README.md)

### OverWatch Integration (Pipeline)
[See Video in Quick Start](#video-guide-and-demonstration-quick-start)

### OverWatch SDK (Python)
* Place [`actions.py`](ow-core/library/actions.py) in the top level of your project directory or python interpreter site packages.
* If necessary, place a blank `__init__.py` file in the same area to make `actions.py` importable.
* In the future, OverWatch is planned to be included in the `PyPI`
* [Link to OverWatch SDK Library docs](ow-core/library/README.md)

### OverWatch Sample Actions
The easiest way to install the sample OverWatch actions into your AWS account is to naviagte on an AWS shell environment to the `ow-actions-cdk` folder, then type in the following command:
```
$ cdk deploy --all --parameters emailparam=<notif-email-here>
```
See [ow-actions-cdk readme](ow-actions-cdk/README.md) for more specifics.

**NOTE:** Team 3 **strongly recommends** you utilise the AWS Console to create the SNS Topics and Lambda Functions as using an IaC solution is not very usable without significant investment in a creation script.
This is out of scope for OverWatch so please consider the above and proceed as necessary.

### OverWatch Integration (Application)
[See Video in Quick Start](#video-guide-and-demonstration-quick-start)

## OverWatch Validator
[Link to OverWatch Validator README](ow-core/validator/README.md)

## OverWatch Deployer
[Link to OverWatch Deployer README](ow-core/deployer/README.md)

## OverWatch Rules YAML Schema Reference
For a more human-readable reference, refer to this guide on enabling [autocomplete/suggestions on VSCode with the schema](/ow-core/validator/README.md#how-do-i-enable-autocomplete-for-my-rules-files-in-vscode).

[Link to Raw OverWatch Rules Schema Reference](ow-core/validator/internal/schema.yaml)

You can also see an example rule that has also been annotated [here](ow-core/example).

## Unit Testing
This is a `pytest` project so please run `pytest` to run the unit tests within the project.
On the top level of the repository:
```
python3 -m pytest
```

## FAQ
### OverWatch: Cloud Resource and Deployment Pipeline. Secured.
#### Can this replace my existing security controls?
* OverWatch is designed to supplement existing security controls and should not be substituted for any baseline policies.
* OverWatch increases the security coverage of application layer business and security behaviours/state.

#### Can I integrate this with Security Hub/other AWS products?
* Yes, absolutely.
* You can export Cloudwatch events into Security Hub as well as others via Lambda or Event Bridge

#### How does this differ to SIEM products such as Splunk or ELK?
* SIEM solutions generally involve engaging with the security team after the product has been built to develop use cases to monitor.
* We leverage the intimate infrastructure knowledge of the developer in order to produce highly customized use cases catered to the specific business itself.
* OverWatch’s threat coverage is unlimited to the needs of your application.

#### How does this differ to other policy control products such as OPA?
* OverWatch differs in that it relies on different processes and ideas to fulfill its purpose.
* OPA expects its users to delegate application logic/decisions to OPA, meaning that a strong integration with the codebase is necessary.
* This leads to significant code refactoring at a big development and downtime cost to the application.

#### How can I be notified if an alarm is triggered?
* You can utilize existing AWS supported integrations such as Slack and Email.
* Alternatively, you can set up automated remediation pipelines via AWS Lambda to your preferred ticketing or response system.
* You can use the AWS SNS Topic to trigger any number of different actions as you wish

#### How do I get started with OverWatch?
* Please see the above [Quick Start Video](#video-guide-and-demonstration-quick-start)

## Architecture
![OverWatch Architecture](overwatch_architecture.png)

## Example Demo Project
You can find an example demo project (Echo) with OverWatch integrated [here](https://github.com/binghub-community/project-echo-demo-app)
