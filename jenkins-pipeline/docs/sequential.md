<!-- .slide: class="center" -->
# Sequential Stages


<!-- .slide: class="dark" -->
<div class="label">Sequential Stages</div>

## Introduction

abc


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