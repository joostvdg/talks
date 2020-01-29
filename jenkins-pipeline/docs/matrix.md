<!-- .slide: class="center" -->
# Matrix Stages


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Introduction

* Extends `Sequential Stages`
* specify multiple sets of values (`axis`)
* run each combination as a stage (Cartesian Product)


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Structure

```groovy
matrix {
    axes { }
    excludes {}
    agent {}
    stages {}
}
```


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Define Axis

```groovy
matrix {
    axes {
        axis {
            name 'JDK_VERSION'
            values '8','11', '13'
        }
        axis {
            name 'JDK_TYPE'
            values 'ibmjava','amazoncorretto', 'jdk'
        }
    }
}
```


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Define Excludes 1/2

```groovy
excludes {
    exclude {
        axis {
            name 'JDK_VERSION'
            values '11'
        }
        axis {
            name 'JDK_TYPE'
            values "ibmjava"
        }
    }
}
```


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Define Excludes 2/2

```groovy
exclude {
    axis {
        name 'JDK_VERSION'
        values '13'
    }
    axis {
        name 'JDK_TYPE'
        notValues 'jdk'
    }
}
```


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## Usecases

* Cross version/OS compilation
* Parallel tests
* ...


<!-- .slide: class="dark" -->
<div class="label">Matrix Stages</div>

## References

* [Jenkins Blog - Introducing Matrix Stages](https://jenkins.io/blog/2019/11/22/welcome-to-the-matrix/)
* [Joost van der Griendt - Jenkins Parallel Pipelines](https://joostvdg.github.io/jenkins-pipeline/jenkins-parallel-pipeline/#parallel-pipeline)
