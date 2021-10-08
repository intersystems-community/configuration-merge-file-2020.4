# InterSystems *Configuration Merge Feature* examples as of InterSystems IRIS 2020.4

-- All examples to be reviewed with the latest InterSystems IRIS version

## Introduction
Each individual subdirectory represents an example of the various configurations and operational activities that are possible with the InterSystems IRIS **configuration merge feature**. The feature is also known as the *CPF merge file* or *configuration state file* as it ultimately allows you to declare the ultimate state of your InterSystems IRIS instances. 

The examples in this Github repo are implemented with containers for ease of use and testing, however, the same technology is available when using the more traditional *tarball-based* distribution. The key factor to the triggering of the *configration merge feature* is the *environment variable* **ISC_CPF_MERGE_FILE**.

This declarative file, that is similar in syntax to the instance CPF, automatically affect the [InterSystems IRIS CPF](https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCPF_INTRODUCTION) (Configuration Parameter File) by merging (a) configuration and (b) architecture changes into InterSystems IRIS instances.

In this repository, each directory is autonomous and contains all that is needed to run each example. 
By cloning or copying the files of each directory, one is able to run that particular example.
Each directory also provides few scripts that help start, stop and reset the environment.

## Considerations
As you can appreciate from the subdirectory names, there are, at a high level, two types of declarations we can use
1) Instance configuration
   - the first three directorries *n-Configuration_**
2) Architecture topologies configurations
   - the last two directories *n-Architecture_**

Examples are provided in container format for DevOps engineers so that we can quickly run them on a single workstation. However, the same *configuration merge feature* and its approach can be leveraged with any configuration management (CM) and automation solution (Chef, Puppet Ansible, Saltstack, Terraform, AWS CloudFormation, etc.) and is leveraged by [InterSystems Cloud Manager (ICM)](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=GICM) with and without containers and with [InterSystems Kubernetes Operator (IKO)](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=PAGE_DEPLOYMENT_IKO).

## Requirements
- Docker
- Docker Compose
- InterSystems IRIS container that can be found at
  - [InterSystems Container Registry](https://containers.intersystems.com)
  - [Docker Hub](https://hub.docker.com/_/intersystems-iris-data-platform)
  - [InterSystems WRC Software Distribution Container page](https://wrc.intersystems.com/wrc/coDistContainers.csp)
- for more advanced architecture topologies (mirroring and shards), an adequate InterSystems IRIS key is required.

