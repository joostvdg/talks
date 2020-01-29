<!-- .slide: class="center" -->
# Parallel Stages


<!-- .slide: class="dark" -->
<div class="label">Parallel Stages</div>

## Introduction

* Built-in Pipeline syntax
* Runs two or more commands in parallel
* Can fail all branches directly when one fails d
* Can use multiple agents in parallel


<!-- .slide: class="dark" -->
<div class="label">Parallel Stages</div>

## Code Example

```groovy
stage('Run Tests') {
    parallel {
        agent {}
        stage('Java 11') {
            steps { }
        }
        stage('Java 13') {
            agent {}
            steps {}
        }
     }
}
```


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/parallel-simple.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark" -->
<div class="label">Parallel Stages</div>

## Parallel PodTemplates

* Run multiple Pods in parallel
* Original Pod is still running...
    * use `agent none` to avoid this
    * but requires *every* `stage` to define an `agent`


<!-- .slide: class="dark" -->
<div class="label">Parallel Stages</div>

## References

* [Jenkins Blog - Introducing Parallel Stages](https://jenkins.io/blog/2017/09/25/declarative-1/)
* [Joost van der Griendt - Jenkins Parallel Pipelines](https://joostvdg.github.io/jenkins-pipeline/jenkins-parallel-pipeline/#parallel-pipeline)