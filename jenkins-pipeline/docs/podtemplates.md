<!-- .slide: class="center" -->
# PodTemplates & Core

<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## What

...


<!-- .slide: class="dark" -->
<div class="label">PodTemplates & Core</div>

## Where

* the Kubernetes plugin itself contains a base template, containing the `jnlp-agent` container
* the Operations Center has a `Shared Kubernetes Cloud` configuration, containg `Shared PodTemplates`
* a master has a Kubernetes cloud configuration, if connected to an Operations Center, it is derived from there
* you can store the YAML definitions of a PodTemplate in a Shared Library, see example below
* you can manage the PodTemplate in your applications' repository


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/podtemplates-where.png" data-background-size="contain" data-background-color="#FFF" -->