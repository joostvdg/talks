<!-- .slide: class="center" -->
# Parallel Stages


<!-- .slide: class="dark" -->
<div class="label">Parallel Stages</div>

## Introduction

abc


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
