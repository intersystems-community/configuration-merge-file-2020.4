# InterSystems Configuration Merge File Examples

## Introduction
Each individual subdirectory represents an example of the various operational activities that are possible with the InterSystems IRIS **Configuration merge file**, also called CPF merge file. 

This declarative file, that is similar in syntax to the instance CPF, automatically affect the default instance [InterSystems IRIS CPF](https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCPF_INTRODUCTION) (Configuration Parameter File) by merging configuration or architecture desired changes into an InterSystems IRIS instance

Each directory is autonomous and contains all that is needed to run each example. 
By cloning or copying the files of each directory one is able to run that particular example.
Each directory also procvides few scripts that help start, stop and reset the environment.

## Considerations
The examples are provided for a simple single-workstation for DevOps engineers so that we can learn quickly, however, the same *configuration merge file* and its approach can be leveraged with any automation solution and with [InterSystems Cloud Manager (ICM)](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=GICM) with and without containers and with [InterSystems Kubernetes Operator (IKO)](https://docs.intersystems.com/irislatest/csp/docbook/DocBook.UI.Page.cls?KEY=PAGE_DEPLOYMENT_IKO).

## Requirements
- Docker and
- Docker Compose
- InterSystems IRIS container that can be found
  - [Docker Hub](https://hub.docker.com/_/intersystems-iris-data-platform)
  - [InterSystems Container Registry](https://containers.intersystems.com)
  - [InterSystems WRC Software Distribution Container page](https://wrc.intersystems.com/wrc/coDistContainers.csp)
- for some more advanced topologies an adequate InterSystems IRIS key is required
-  ...


## 
