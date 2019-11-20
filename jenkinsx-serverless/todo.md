# TODO

## Red Herring

* goal
    * we want to deliver value to customers with consistent quality, short feedback cycles, minimal overhead and developer/ops happy
* challenges
    * there's dozens of languages, frameworks, platforms and so-on to do this for
    * it has been complex, too many tools/frameworks/languages to chose from
    * difficult to create seamless, consistent, easy, standard yet customization friendly way to do this
* solution
    * jenkins x helps by setting out a path, with everything included
    * to use it effectively, you need to understand CI/CD, GitOps, JX Binary & BuildPacks
    * to master it, you need to understand Kubernetes (basics), SDLC and Jenkins X customization options

### Decks

#### Core

* intro
* goals check
* CI/CD basics
    * continuous integration
    * short feedback cycles
    * standardization
    * automation
    * tests
    * pipelines
* Containerization
    * container
    * docker
    * orchestration
    * kubernetes
* JX Intro

#### path to usage

* Core +
* GitOps
* JX explained
* JX Binary
* JX Go Demo
* Kubernetes
    * intro
    * overview
    * demo basic 0
* JX BuildPacks
* JX BuildPack Demo
    * Import
    * Create BuildPack
* JX Dev Workflow
     * DevPod
     * SemVer
     * PR's
     * Workflows & BuildPacks
* JX DevPod demo

#### path to mastery

* Core +
* Kubernetes
* SDLC
* My Journey to JX
* GitOps
* JX explained
* JX Opinions
* JX Binary
* Pipelines
    * investigate JX pipeline
    * best practices
* JX Go Demo
* Kubernetes
    * intro
    * overview
    * demo basic 1
    * demo basic 2
    * demo basic 3
* JX BuildPacks
* JX BuildPack Demo
    * Import
    * Create BuildPack
* JX - The X-Files Demo
* JX Serverless vs. Static
* Contents of .jx folder
* K8S ecosystem deep dive
    * limited to the tools used by JX
    * Kaniko
* JX Dev Workflow
     * DevPod
     * SemVer
     * PR's
     * Workflows & BuildPacks
* JX DevPod demo
* JX Production ready
    * JX GitOps
    * JX Terraform?
    * Kubernetes Advanced
        * Annotations
        * PolicyAgent
        * PodSecurityPolicy
        * NetworkPolicy

#### Concepts to cover

See https://jenkins-x.io/about/concepts/

* Self-Service
* Loosely-coupled
* Event Driven
* Automation
* Trunk Based Development, PR's & Feature Flags
* Immutable Infrastructure
* Infrastructure As Code
* Pipeline As Code
* 12-Factor App/Container
* Shift Left
* Percentage Based Timecard
    * i.e. 50% work, 20% refactor, 10% defects,...


##### From JX

* Loosely-coupled Architectures
* Self-service Configuration
* Automated Provisioning
* Continuous Build / Integration and Delivery
* Automated Release Management
* Incremental Testing
* Infrastructure Configuration as Code
* Comprehensive configuration management
* Trunk based development and feature flags

## From Vincent

* CI/CD
    * building/publishing artifacts
    * releases (release notes), semver & tagging
* jenkins pipeline
    * the issue with "old/classic" jobs defined through the UI. Everything in git
    * syntax, DSL: stages, steps, environment, credentials, parallel. best practices
    * pipeline & github: auto jobs creation (branches/PR discovery), diff between building a branch and a PR (merge master)
* running pipelines in kube
    * everything is a container: definition of the pod spec in the jenkinsfile, and new "container" keyword
* GitOps
* static envs vs dynamic envs. For the moment everybody is used to static envs. I think it’s important to show the advantage of dynamic env. Could be a good intro to preview envs

* Cron-based Jenkins jobs: we have quite a few right now (I need to go over all our current jobs with you). Prefer event-based over scheduled. What if we have some jobs we really want to schedule?

* gcloud SDK (CLI). A few of us are used to it, but most people never used it. Because it’s also our client for things like pubsub or GCS, it might be good to have a (small) part about google cloud, and how to use it. There is also the “service account” part that I mentioned (in the “pushing to GCR” part), that is related.

* in the “Jenkins x” part, it would be great if we can show an example of using updatebot. That’s a great tool, and I love how the Jenkins x project is using it to automate the versions updates everywhere, and I’d love to do the same thing.


## URLS

file:///Users/joostvdg/Projects/Personal/Github/jenkinsx-workshop/index.html
http://127.0.0.1.nip.io:8090/docs/k8s/
https://github.com/the-jenkins-x-files/workshop
https://github.com/the-jenkins-x-files/workshop/blob/master/mulder/import.md
https://github.com/joostvdg/mulder
https://www.weave.works/blog/managing-helm-releases-the-gitops-way
https://www.weave.works/blog/gitops-operations-by-pull-request
https://www.weave.works/blog/what-is-gitops-really
https://www.weave.works/technologies/gitops/

## Kubernetes Basics

### Slides

### Demos

* validate tools & versions (kubectl, helm, jx)
* validate access to cluster (kubectl config)
* validate state of cluster (kubectl get nodes -o wide)
* Creating Pods
* Scaling Pods With ReplicaSets
* Using Services To Enable Communication Between Pods
* Deploying Releases With Zero-Downtime
    * Deployment
* Building Docker Images
    * docker
    * build-kit
    * kaniko
* Using Ingress To Forward Traffic
* Using ConfigMaps To Inject Configuration Files
* Using Secrets To Hide Confidential Information
* Dividing A Cluster Into Namespaces
* Securing Kubernetes Clusters
* Managing Resources
* Persisting State
* Deploying Stateful Applications At Scale

## Scully

* fork & clone
* jx import
* fix Dockerfile
* add Mulder as dependency
    * helm repo stuff
* fix url to Mulder
* click on Scully's "voice box" to get a quote...

### Fix nodejs in mac

!!! Warning
    ```bash
    internal/modules/cjs/loader.js:583
    throw err;
    ^

    Error: Cannot find module '../lib/utils/unsupported.js'
        at Function.Module._resolveFilename (internal/modules/cjs/loader.js:581:15)
    ```

```bash
sudo rm -rf /usr/local/lib/node_modules/npm
brew reinstall node
```

## Mulder

* fork
* clone
* import into jx
* fix redis config
* fix health check endpoint
* add unit tests to pipeline
* add integration tests to pipeline
* test PR
* test staging & production

### Change to Continuous Deployment

> So our current pipeline is doing Continuous Delivery, not Continuous Deployment: you still need to run a manual command to deploy to production. What if we want to switch to continuous deployment? We have 2 solutions:

* Update the production environment's configuration, using the `jx edit environment production` command, to switch to Auto promotion - that will apply to all applications.

* Update the Jenkinsfile of an application to run the `jx promote --env production` command right after the jx promote `--all-auto` command - this will only apply to that single application.

## Questions

* do we need the `jx helm build` stuff?