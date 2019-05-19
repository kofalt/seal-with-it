# Seal With It

![](ci-badge) ![](godoc) ![](report-card) _Project status: the Seals are not ready for you yet. You're too early. Check back later, friend._

![And I looked, and behold, a pale seal! And its rider's name was podman, and k8s followed him.](https://i.imgur.com/hZntntm.gif)

## What is it?

You know when you try to locally run the infrastructure at your latest company / meetup / hangout?<br/>
You've probably experienced the same problems, over and over again:

* The "project" is a miserable pile of repos
* One of these repos is special, and crudely lashes together the others
* There's probably one monolithic entry point, which obscures how bootstrapping works
* Setup takes 30 years and more bandwidth than your first computer had hard drive space
* Your luxury-margin laptop fans fly to the moon and Skype or whatever runs out of memory
* It probably calls `docker` or `apt` somewhere in there, so now the pile of misery needs root

Seal hopes to do a little better than this.

![](demo.jpg)

## What does it do?

Seal uses [Podman](https://github.com/containers/libpod) to present a lean, mean, dashboard ~machine~ view on your environment.<br/>
Seal is good at:

* Only running the subset of the project that you care about
* Presenting log output in a sane and readable way
* Unifying live-reload and automatic compilation / testing across your components
* Managing this in real time with an easy CLI GUI

You take care of defining a reasonable OCI layout for your project; Seal takes care of you.

## Installation (linux)

1. Install podman via their instructions [here](https://github.com/containers/libpod/blob/master/install.md).
1. Check that you get a shell: `podman run -it --rm docker.io/ubuntu bash` _(no root required!)_

----

# OK the seals are in trouble

![MRW no seals](https://i.imgur.com/4C31r39.jpg)

The rest of this readme doesn't apply for now because there are a few podman things to iron out:

* https://github.com/containers/libpod/issues/2963
* https://github.com/containers/libpod/issues/3126
* https://github.com/containers/libpod/issues/3157

Kube compat stuff is on hold _check back later_


<!-- Build the proj -->

## Installation (vagrant)

<!--  -->

## Setting up your project

<!--  -->

## Logging

![Seals and logs are natural frenemies.](https://i.imgur.com/kcisDVM.jpg)

Your project's logging situation is a cancerous mess. It's OK. Don't cry. We're all in this together.<br/>
The seals have heard your plea, and in their mighty Seal Wisdom let you modify logs on the fly:
<!--
```yaml

```
 -->
These rules take affect in-memory before logging is shown on screen.<br/>
If you ever need to bypass this, `podman logs` will still show The Real Deal.

## Path to production

![Seals deploying to production](https://i.imgur.com/xBlrYYZ.gif)

Seals tend not to have opinions about production ecosystem design.<br/>
However, the good nes is that your `podman` pod files are [compatible](https://github.com/containers/libpod/blob/master/docs/podman-generate-kube.1.md) with [Kubernetes](https://kubernetes.io).<br/>
This allows for a fairly-trivial path to production, should you desire:

<!-- Demo

podman generate kube XYZ  > production.yml

kubectl create -f production.yml

-->

There is a detailed blog post about this approach by the Red Hat Developer group [here](https://developers.redhat.com/blog/2019/01/29/podman-kubernetes-yaml).

## I dislike seals, get out of my way!

![MRW someone doesn't like seals](https://i.imgur.com/x97Cwkd.gif)

<!-- Hah, this image needs shrinking ^, Github gets mad -->

Not everyone is a fan of our aquatic marine mammals. This is unfortunate, but unavoidable.<br/>
Luckily, there's no magic to what Seal does: it all runs off a standard podman Pod file.

If your team has Sealed up their local environment, you can happily ignore them by calling `podman` directly:


To disable specific services the way a Seal would, just comment out parts of the file.
