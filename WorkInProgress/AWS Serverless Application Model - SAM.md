

# AWS Serverless Application Model - SAM

### Build serverless applications in simple and clean syntax

[Get started with AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started.html)

The AWS Serverless Application Model (SAM) is an open-source framework for building serverless applications. It provides shorthand syntax to express functions, APIs, databases, and event source mappings. With just a few lines per resource, you can define the application you want and model it using YAML. During deployment, SAM transforms and expands the SAM syntax into AWS CloudFormation syntax, enabling you to build serverless applications faster.

To get started with building SAM-based applications, use the [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-reference.html#serverless-sam-cli). SAM CLI provides a Lambda-like execution environment that lets you locally build, test, and debug applications defined by SAM templates or through the AWS Cloud Development Kit (CDK). You can also use the SAM CLI to deploy your applications to AWS, or create secure continuous integration and deployment (CI/CD) pipelines that follow best practices and integrate with AWS' native and third party CI/CD systems.

SAM and SAM CLI are open-sourced under the Apache 2.0 license. You can contribute new features and enhancements to [SAM on GitHub](https://github.com/awslabs/serverless-application-model) or [SAM CLI on GitHub](https://github.com/awslabs/aws-sam-cli).

**Getting Started with SAM**

# Install SAM CLI

[Mac](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-mac.html)

Install SAM CLI using Brew

> brew tap aws/tap

> brew install aws-sam-cli

Requires Docker and the AWS CLI. [See installation instructions](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-mac.html)

[Linux](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-linux.html)

Install SAM CLI by downloading a ZIP file

- [aws-sam-cli-linux](https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip)

Requires Docker and the AWS CLI. [See installation instructions](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-linux.html)

[Windows](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-windows.html)

Install SAM CLI using an MSI

- [64 bit](https://github.com/awslabs/aws-sam-cli/releases/latest/download/AWS_SAM_CLI_64_PY3.msi)

Requires Docker and the AWS CLI. [See installation instructions](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install-windows.html)

[AWS CDK support (Preview)
](https://docs.aws.amazon.com/cdk/latest/guide/getting_started.html)

Use AWS SAM CLI to [build and test applications](https://aws.amazon.com/blogs/compute/better-together-aws-sam-and-aws-cdk/) defined using AWS CDK.

- [Download](https://github.com/aws/aws-sam-cli/releases/tag/sam-cli-beta-cdk)

Requires Node Package Manager. [See installation instructions](https://docs.aws.amazon.com/cdk/latest/guide/getting_started.html#getting_started_install)

# Why SAM?

**Single Deployment Configuration**

Use SAM to organize related components, share configuration such as memory and timeouts between resources, and deploy all related resources together as a single, versioned entity.

**Integration with Development Tools**

SAM integrates with a suite of AWS serverless tools. Find new applications in the [AWS Serverless Application Repository](https://serverlessrepo.aws.amazon.com/applications), use [AWS Cloud9](https://aws.amazon.com/cloud9/) IDE to author, test, and debug SAM-based serverless applications, and [AWS CodeBuild](https://aws.amazon.com/codebuild/), [AWS CodeDeploy](https://aws.amazon.com/codedeploy/), and [AWS CodePipeline](https://aws.amazon.com/codepipeline/) to build a deployment pipeline. To start with a project structure, code repository, and CI/CD pipeline configured for you, try [AWS CodeStar](https://aws.amazon.com/codestar/).

**Local Testing and Debugging**

Use SAM CLI to step-through and debug your code. It provides a Lambda-like execution environment locally and helps you catch issues upfront. 

**Built on AWS CloudFormation**

AWS SAM is an extension of AWS CloudFormation, so you get the reliable deployment capabilities of CloudFormation. You can also define resources using CloudFormation in your SAM template and use the full suite of resources, intrinsic functions, and other template features that are available in AWS CloudFormation.

**Built-In Best Practices**

Deploy your infrastructure as config to leverage best practices such as code reviews. Enable gradual deployments through AWS CodeDeploy and tracing using AWS X-Ray with just a few lines of SAM config.

# Contribute to SAM

[Enhance the SAM Specification](https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md)

Make pull requests, report bugs, and share ideas to improve the full AWS SAM template specification

[Strengthen SAM CLI](https://github.com/awslabs/aws-sam-cli)

Add new commands or enhance existing ones, report bugs, and improve documentation for the SAM CLI

Want to dive into the docs or watch a SAM tutorial? 

[Visit the SAM resources page](https://aws.amazon.com/serverless/sam/resources/)

Have more questions?

[Contact us](https://aws.amazon.com/contact-us/)

### Learn About AWS

- [What Is AWS?](https://aws.amazon.com/what-is-aws/?nc1=f_cc)
- [What Is Cloud Computing?](https://aws.amazon.com/what-is-cloud-computing/?nc1=f_cc)
- [AWS Inclusion, Diversity & Equity](https://aws.amazon.com/diversity-inclusion/?nc1=f_cc)
- [What Is DevOps?](https://aws.amazon.com/devops/what-is-devops/?nc1=f_cc)
- [What Is a Container?](https://aws.amazon.com/containers/?nc1=f_cc)
- [What Is a Data Lake?](https://aws.amazon.com/big-data/datalakes-and-analytics/what-is-a-data-lake/?nc1=f_cc)
- [AWS Cloud Security](https://aws.amazon.com/security/?nc1=f_cc)
- [What's New](https://aws.amazon.com/new/?nc1=f_cc)
- [Blogs](https://aws.amazon.com/blogs/?nc1=f_cc)
- [Press Releases](https://press.aboutamazon.com/press-releases/aws)

