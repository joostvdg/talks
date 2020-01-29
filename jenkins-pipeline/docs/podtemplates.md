<!-- .slide: class="center" -->
# PodTemplates & Core


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## What

* Ephemeral Build Agents within Kubernetes
* Via [OSS plugin](https://github.com/jenkinsci/kubernetes-plugin)
* Agents are launched using JNLP
* Depends on `Kubernetes Cloud Configuration`
* Creates Kubernetes Pod & mounts temporary Workspace


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Benefits

* Only consume resources when there's a build
* Only need a docker image to build
* Workspace is automatically cleaned up
* One tool per container
    * easy to compose build environment
    * less complex to maintain


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## How

* Can be defined in multiple ways
    * Programmatically
    * Via Yaml
* Templates can be inherited/extended
* Pods can be re-usable
    * in build
    * across builds


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Where

* Jenkins Kubernetes plugin itself
* Operations Center -> `Shared PodTemplates`
* Master -> `PodTemplates`
* YAML definitions in a Shared Library
* PodTemplate in your `Jenkinsfile`


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/podtemplates-where.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Docker-in-Docker 1/2

* Don't do it
* Unless you really really have to
* Then only to ease transition


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Docker-in-Docker 2/2

* Don't do it Docker-On-Docker
* Do Docker-In-Docker (`DIND`)
    * `runtime` container
    * `client container`
    * both in the PodTemplate


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Docker-in-Docker Example

```groovy
agent { kubernetes {
    yaml """containers:
            - name: docker-client
                image: docker:19.03.1 
            - name: docker-daemon
                image: docker:19.03.1-dind
    """}}
stages { stage ('build') {
    steps { container('docker-client') {
        sh 'docker image build  -t myImage .  '
    }}
}}
```


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## References

* [CloudBees Core Workshop](https://github.com/cloudbees-days/cloudbees-core-workshop/blob/master/catalog-templates.md)
* [CloudBees Core Documentation](https://docs.cloudbees.com/docs/cloudbees-core/latest/cloud-admin-guide/agents#kubernetes-agents)
* [Jerome Petazzo - Docker In Docker](https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/)
* [Joost van der Griendt - Docker In Docker](https://joostvdg.github.io/jenkins-pipeline/podtemplate-dind/#docker-in-docker-with-podtemplates)
* [Joost van der Griendt - Docker Build Alternatives](https://joostvdg.github.io/blogs/docker-alternatives/)
