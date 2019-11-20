<!-- .slide: class="center" -->
# jx boot


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## What Is It

* GitOps<!-- .element: class="fragment" -->
* Configuration-as-Code<!-- .element: class="fragment" -->
* for your apps<!-- .element: class="fragment" -->
* your env... <!-- .element: class="fragment" -->
* and your CI/CD!<!-- .element: class="fragment" -->


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## What Does It Contain

* Configuration Repository (bootstrap)
* Development Environment Repository (Dev)
* External DNS (cloud dns)
* Secrets Vault (Hashicorp Vault)


<!-- .slide: class="center light" -->
<!-- .slide: data-background="img/jx-boot-process.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## How To Start

* Have a Kubernetes cluster
* Run `jx boot` to initialize
* Adjust `jx-requirements.yml`
* Run `jx boot` from *configuration repository*


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## JX Requirements

* Cluster
* Ingress
* Enviroments
* General
* Storage (optional)


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## Cluster

```yaml
cluster:
  clusterName: mycluster
  environmentGitOwner: joostvdg
  gitKind: github
  gitName: github
  gitServer: https://github.com
  namespace: jx
  project: my-gcp-project
  provider: gke
  zone: europe-west4
```


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## Ingress

```yaml
ingress:
  domain: dev.example.com
  externalDNS: true
  namespaceSubDomain:  "."
  tls:
    email: me@example.com
    enabled: true
    production: true
```


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## Environments

```yaml
environments:
- key: dev
- key: staging
  repository: env-cjxd-staging
- key: production
  repository: env-cjxd-production
  ingress:
    domain: prod.mydomain.com
    ...
```


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## General

```yaml
gitops: true
kaniko: true
secretStorage: vault
bootConfigURL: https://github.com/cloudbees/...-boot-config.git
```


<!-- .slide: class="dark center" -->
<div class="label">boot</div>

## Storage

```yaml
storage:
  backup:
    enabled: false
    url: ""
  logs:
    enabled: true
    url: gs://joost-cjxd-logs-a36d3a84-48ab-4a18-8e6c-b88e63bd81bb
```
