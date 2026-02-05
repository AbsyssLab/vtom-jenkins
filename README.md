# Jenkins Integration with Visual TOM
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE.md)&nbsp;
[![fr](https://img.shields.io/badge/lang-fr-yellow.svg)](README-fr.md)  
This project provides an integration between **Visual TOM** and **Jenkins** to trigger Jenkins jobs from Visual TOM jobs using the `jenkins-cli.jar` tool.

# Disclaimer
No Support and No Warranty are provided by Absyss SAS for this project and related material. The use of this project's files is at your own risk.

Absyss SAS assumes no liability for damage caused by the usage of any of the files offered here via this Github repository.

Consultings days can be requested to help for the implementation.

# Prerequisites

  * Visual TOM **7.1.2 or higher**
  * Jenkins CLI binary to be downloaded from your Jenkins server:  
    ```
    http://jenkins-server:port/jnlpJars/jenkins-cli.jar
    ```
    Place the binary into the `%ABM_BIN%` directory.
  * Java compatible with your Jenkins version:  
    [Jenkins – Support Policy Java](https://www.jenkins.io/doc/book/platform-information/support-policy-java/?utm_source=chatgpt.com)

# Instructions

Define the following variables on the agent running Jenkins jobs:

  ```Environment variables to declare
JENKINS_URL=http://<jenkins-server>:<port>
JENKINS_USER_ID=XXXX
JENKINS_API_TOKEN=34654564XXXXX21231321
JAVA_JENKINS=F:\openlogic-openjdk-jre-17.0.12+7-windows-x64\bin\java
  ```

The file **jenkins.xml** is the Jenkins job template to be imported into your Visual TOM repository.
It takes one argument corresponding to the Jenkins job name.

The queue script **submit_queue_jenkins.bat** must be deployed and declared on the Windows agent.

# Available Actions

## Global Objective
The batch queue encapsulates the execution of the jenkins-cli.jar binary with the build argument, which allows triggering a Jenkins job.

## Arguments
In the model, only one input parameter is required: the name of the Jenkins job.

The build Command Allows You To:
- ➡️ Trigger a Jenkins job
- ➡️ Optionally pass parameters
- ➡️ Wait for the build to complete
- ➡️ Control the behavior (logs, failures, timeouts, etc.)

## Résultat du job	Code CLI

| Job Result | CLI Exit Code |
| ---------- | ------------- |
| SUCCESS    | 0             |
| FAILURE    | ≠ 0           |
| ABORTED    | ≠ 0           |
| TIMEOUT    | ≠ 0           |

# License
This project is licensed under the Apache 2.0 License - see the [LICENSE](license) file for details


# Code of Conduct
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.1%20adopted-ff69b4.svg)](code-of-conduct.md)  
Absyss SAS has adopted the [Contributor Covenant](CODE_OF_CONDUCT.md) as its Code of Conduct, and we expect project participants to adhere to it. Please read the [full text](CODE_OF_CONDUCT.md) so that you can understand what actions will and will not be tolerated.
