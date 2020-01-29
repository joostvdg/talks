<!-- .slide: class="center" -->
# Sequential Stages


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## Introduction

* Extends Parallel stages
* Allows creating parallel *streams*
    * parallel set of stages executed sequentially
    * enables everything that `stages {}` can do


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## Code Example - Simple

```groovy
stages {
    stage('Checkout') {
        stage('Run Tests') {
            parallel {
                stage('Java 11') {
                    stages {
                        stage('Build') {
                            steps {}
                        }
                    }
                }
            }
        }
    }
}
```


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/parallel-sequential-1.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## Complex Cases

* Start with `agent none` at Pipeline root
* Now every `stages` needs a `agent`
* Except: when encapsulated by a `Parallel Sequential` stage


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## Code Example - Complex

```groovy
pipeline {
    agent none
    stages {
        stage('Build & Test') {
            stage('Parallel') {
                parallel {
                    stage('Java 11') {
                        agent {}
                        stages {}
                    }
                    stage('Java 11') {
                        agent {}
                        stages {}
                    }
                }
            }
        }
    }
}
```


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/parallel-sequential-2.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## With PodTemplates

* Same as above, agent none + agent per `parallel stream`
* PodTemplates as agents
* Allows re-use within/across builds
    * set `idleMinutes` and `activeDeadlineSeconds`
    * set `label` to something unique for this build
* avoid creating Pod via `when{}` + `beforeAgent true`


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

##  BeforeAgent Example

```groovy
stage('deploy') {
    when {
        branch 'master'
        beforeAgent true
    }
    agent {kubernetes { label 'abc'} }
    steps {}
}
```


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/parallel-sequential-2.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## References

* [Jenkins Blog - Introducing Sequential Stages](https://jenkins.io/blog/2018/07/02/whats-new-declarative-piepline-13x-sequential-stages/)
* [Joost van der Griendt - Jenkins Parallel Pipelines](https://joostvdg.github.io/jenkins-pipeline/jenkins-parallel-pipeline/#parallel-pipeline)