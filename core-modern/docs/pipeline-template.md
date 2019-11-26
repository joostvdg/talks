<!-- .slide: class="center" -->
# Pipeline Template


<!-- .slide: class="dark center" -->
<div class="label">Template</div>

## What It Is

* Template Catalog
* Markerfile


<!-- .slide: class="dark center" -->
<div class="label">Template</div>

## Template Catalog


<!-- .slide: class="center dark" -->
<!-- .slide: data-background="../img/core/template-catalog-structure.png" data-background-size="contain" data-background-color="#FFF" -->


<!-- .slide: class="dark center" -->
<div class="label">Template</div>

## Template Catalog

```yaml
version: 1
type: pipeline-template
templateType: MULTIBRANCH
name: javaMavenMultibranch
parameters:
  - name: mavenAdditionalTargets
    type: string
    displayName: Additional Maven build targets
  - name: repoName
    type: string
    displayName: GitHub repository name
  - name: repoOwner
    type: string
    displayName: GitHub repository owner
  - name: gitCredentialsId
    type: credentials
    displayName: CredentialsID for GitHub
multibranch:
  branchSource:
    github:
      repoOwner: ${repoOwner}
      repository: ${repoName}
      credentialsId: ${gitCredentialsId}
```