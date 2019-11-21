<!-- .slide: class="center" -->
# Cross-Team Collaboration


<!-- .slide: class="dark center" -->
<div class="label">X-Team</div>

## What It Is

* ?


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/core/cross-team-diagram.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark center" -->
<div class="label">X-Team</div>

## Create JSON Event

```groovy
publishEvent jsonEvent('{"eventName":"helloWorld"}')
```


<!-- .slide: class="dark center" -->
<div class="label">X-Team</div>

## Trigger on JSON Event

```groovy
triggers {
    eventTrigger jmespathQuery("eventName=='helloWorld'")
}
```


<!-- .slide: class="dark center" -->
<div class="label">X-Team</div>

## External Endpoints

* create endpoints on CJOC
* set of predefined listeners
    * dockerhub
    * artifactory


<!-- .slide: class="center light" -->
<!-- .slide: data-background="../img/core/xteam-external-endpoints.png" data-background-size="contain" data-background-color="#FFF" -->
