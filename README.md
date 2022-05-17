# UW Boost

Welcome to the UW Boost guide, or how to get jump started with technology at UW. Below are a collection of resources that will be useful to work on our tech stack. This is intended for people new to these technologies as well as anyone with experience looking for a bit of a cheat sheet.

99% of all our services are written in Go, while the frontend is React, glued together with GraphQL. At the moment this guide will focus on the two most important aspects for the majority of our developers Go and K8s.

## Our Stack

**Infrastructure**
-   K8s (Kubernets)
-   Terraform
-   AWS (Amazon Web Services)
-   GCP (Google Cloud Platform)
-   On Prem

**The Backend**
-   Go (GoLang)

**The Frontend**
-   React
-   Typescript
-   GraphQL

# Infrastructure

## Kubernetes (k8s)

A key concept to understand when working with k8s is that of a **namespace** and a **context**. In theory you could setup a unique context for each namespace/cluster combination but most users tend to have one context per cluster and then use the namespace flag to ensure they are accessing the correct namespace within the correct cluster.

For example say we had the following clusters

-   Dev Cloud
-   Prod Cloud
-   Dev On Prem
-   Prod On Prem

The contexts could be dev-cloud/prod-cloud and dev-prem/prod-prem

Within each cluster there are multiple namespaces, for example team-a and team-b.

So if you wanted to know what pods are running in team-a's namesapce on dev-cloud you would run

```sh
kubectl --context=dev-cloud -n team-a get po
```

Once you've found a pod you are looking for and want to know more, you can describe it.

```sh
kubectl --context=dev-cloud -n team-a describe po my-cool-pod
```

If for example you wanted to force your my-cool-pod to restart you can kill the current instance

```sh
kubectl --context=dev-cloud -n team-a kill po my-cool-pod
```

Assuming your pod is setup to have one active instance this causes kubernets to kill the pod you requested and schedule another in its place.

Another way of interacting with k8s is by using the CLI tools [**k9s**](https://k9scli.io) which provides a powerful and intuitive terminal GUI interface. It can be installed via brew

```sh
brew install k9s
```

Like k8s you can start it with your desired context and namesapce

```sh
k9s --context=dev-cloud -n team-a
```

k9s has its own documentation but labeling and keyboard shortcuts are pretty self explanitory.

# The backend

## Go

For those that cherish the classroom experience Udemy has a great course that covers a range from fundamentals all the way to advanced language features.

-   [Learn How To Code](https://www.udemy.com/course/learn-how-to-code/)

For people that prefer the rustle of paper and self directed learning then the best place to start is _the_ Go book

-   [The Go Programming Language](http://www.gopl.io/)

Finally for the hybrid person who wants self directed learning with an interactive element, Exercism has a good Go track. This is also a great way to learn how tests are written in Go as each exercise comes with the tests, for which you need to write code that passes them.

-   [Go on Exercism](https://exercism.org/tracks/go)
