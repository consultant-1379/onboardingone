INTRODUCTION

A shared library helps to re-use parts of pipeline allowing pipeline code to be small and easy to maintain. This solution has been added to ci-pipeline-jenkins-config repository which is declared within the Global Variables directory (vars).
Creation of groovy file in vars declares Global Variables that are ready to be used once the shared library is imported
Functions that are declared within this groovy file can be called from any where in pipeline script.


USAGE

In Jenkins: Shared Library is defined with a name: ci-pipeline-lib with master branch as Default version.
This configuration is defined under Manage Jenkins » Configure System » Global Pipeline Libraries 
SCM plugin is used load/retrive the library.

Pipeline Jobs: @Library annotation is used in Pipeline Jobs to specify library’s name.
Libraries are resolved and loaded during compilation of the script, before it starts executing. This allows the Groovy compiler to understand the meaning of symbols used in static type checking, and permits them to be used in type declarations in the script,for example:
@Library('ci-pipeline-lib') _


FUNCTIONALITY

ci-pipeline-jenkins-config contains 3 main processes:
1) Jenkinsfile - pipeline configuration file - defines stages in pipeline jobs.
Each stage contains methods / scripts that are versioned controlled in ci-pipeline-lib and uses variables defined in pipeline_global.cfg and pipeline_local.cfg
2) projects_file is a list of all the repos that has CI/CD pipeline jobs - both repos from New Product/Repo Request app and repos that migrate to the CI/CD Pipeline 
3) DSL Seed job - it is the backbone of the pipeline - by connecting various elements together it creates pipeline jobs for every repo in the projects_file. There is one DSL Seed Job per each type of the pipeline - Release, PCR unit, PCR integration etc.

MAINTAINERS

Team: DE-Axis Ops
DL  : OSS-Axisops@wipro.com or 
      PDLDEAXISO@pdl.internal.ericsson.com
