# Kubernetes At Home!

This guide is a curated list of tools to run and experiment with Kubernetes. It assumes you already have cursory knowledge of containerization and Docker, and its goal is to help you build your path forward.

## What is Kubernetes?

Kubernetes (often abbreviated as "k8s", though pronounced identically) is an open-source collection of tools which "orchestrate" (manage) application containers across a cluster of computers, providing layers of abstractions to make management of those applications as easy as possible, from the perspectives of both an application developer and a platform operator.

**tl;dr:** it runs containers really well.

## Why is Kubernetes?

In the beginning, infrastructure was simply physical computers, and there was software to manage those physical computers. Next came virtual machines, and software to manage virtual machines. Most of that same physical computer software worked for VMs, but as the technology matured, specialized software was created instead. The next iteration of infrastructure is containers, and virtual machine software is no longer good enough. Kubernetes is the newest generation of software that manages the next generation of infrastructure abstraction that is containers.

**tl;dr:** effectively managing lots of containers is hard.

## What are my options?

The popularity of Kubernetes has exploded in the past couple years as organizations move to containerize and restructure their application platforms. This is great news for you, because it means there is a hugely diverse field of tools to choose from.

This guide is structured around matching a Kubernetes offering around your experience level and your ultimate goal. There are a lot of options when it comes to "running Kubernetes," so pick a description that best matches your thoughts to narrow the list down:

- _[I have no idea what I'm doing.](#i-have-no-idea-what-im-doing)_
- _[I want to use the same computer I do my work on.](#i-want-to-use-the-same-computer-i-do-my-work-on)_
- _[I want to use my own hardware.](#i-want-to-use-my-own-hardware)_
- _[I want to use ✨the cloud.✨](#i-want-to-use-the-cloud)_

### I have no idea what I'm doing.

That's okay! [Docker Desktop] and [minikube] both are great places to start. Both of them handle the nitty-gritty of Kubernetes administration for you, and enable you to ease your way into experimentation.

- **[Docker Desktop]**

  Docker added [built-in support for Kubernetes] in late 2018. If you've got it installed already, you can enable Kubernetes support in the Docker Desktop settings. It comes with a bundled version of kubectl that will stay up-to-date with Docker's version of Kubernetes.

  Keep in mind that using Kubernetes in Docker Desktop is meant more for local development than running a fully fledged, outside-accessible cluster. If you want to run long-standing deployments, you should consider a more advanced option.

- **[minikube]**

  minikube is the officially provided CLI tool that runs a single-node Kubernetes cluster locally, inside of a virtual machine. It doesn't provide most of the complex aspects of managing a Kubernetes cluster, but it is perfectly fine for getting the hang of deploying containers to a Kubernetes cluster.


[Docker Desktop]: https://www.docker.com/products/docker-desktop/
[built-in support for Kubernetes]: https://docs.docker.com/docker-for-mac/#kubernetes
[minikube]: https://minikube.sigs.k8s.io/docs/

### I want to use the same computer I do my work on.

If you have some experience with Kubernetes already, you might consider some more complex tools to run Kubernetes on your machine.

- **[kind]**

   kind is still in beta as of this writing in August 2020, but is looking to become a solid alternative to minikube. The two are similar, but kind strips out the virtual machine aspect, and supports more than one node. It runs fully-featured Kubernetes nodes on your computer directly as Docker containers, using [kubeadm] within the node containers. This means kind offers a more production-like Kubernetes experience compared to minikube, but has additional complexity that may slow you down.

- **[MicroK8s]**

  MicroK8s is a Kubernetes distribution developed by Canonical (who also maintain [Ubuntu]). It comes with a CLI tool `microk8s`, an image registry, and an add-ons system. MicroK8s offers more flexibility than either Docker Desktop or minikube, allowing you to easily expand to more nodes if you decide to stand up a Kubernetes cluster long-term.


[kind]: https://kind.sigs.k8s.io/
[MicroK8s]: https://microk8s.io/
[Ubuntu]: https://ubuntu.com/

### I want to use my own hardware.

If you have hardware to spare, running Kubernetes directly can be an involved (but very rewarding!) experience. These tools offer the real deal of Kubernetes, some with more shortcuts than others.

- **[k3s]**

  k3s is "five less than k8s," to emphasize what it abstracts away from vanilla Kubernetes — relatively tedious things like managing certificates, DNS, and ingress controllers. k3s is unique in that it's targeted at Raspberry Pi and similar microcomputers, so if you want a cluster but don't need a lot of horsepower, you can get up and running without spending much money.

- **[kubeadm]**

  kubeadm is the first-party utility for bootstrapping a Kubernetes cluster. It's not for the faint of heart; it is an incredibly powerful and complex tool. It gives you full control of provisioning (i.e. requires that you configure) a Kubernetes cluster — certificates, networking; literally everything Kubernetes offers — so it's only for those who love customization or the truly devoted.


[k3s]: https://k3s.io/
[kubeadm]: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/

### I want to use _✨the cloud.✨_

Running on the cloud is best if you neither have nor want your own hardware for Kubernetes, but can be cost-prohibitive in some cases.


- **[DigitalOcean]** offers an easy-to-use, startup-scale managed Kubernetes offering.

- **[Azure AKS]**, **[Google Cloud GKE]**, and **[Amazon EKS]** are among the many enterprise-scale managed Kubernetes offerings. Like any cloud service provider, they are highly configurable, but might be best only if your employer is footing the bill.

[DigitalOcean]: https://www.digitalocean.com/products/kubernetes/
[Azure AKS]: https://azure.microsoft.com/en-us/services/kubernetes-service/
[Amazon EKS]: https://aws.amazon.com/eks/
[Google Cloud GKE]: https://cloud.google.com/kubernetes-engine/


## Resources once you're set up

- If the concept of Kubernetes is still confusing (and it's okay if it is!), read _[The Illustrated Children's Guide to Kubernetes]_ and _[Phippy Goes to the Zoo]_. Both books are published by the [Cloud Native Computing Foundation], the nonprofit organization that takes primary ownership of Kubernetes and some of its ecosystem of tools. Don't let the names fool you, they are great sources to help people of all ages understand Kubernetes.
- The _[Learn Kubernetes Basics]_ section of the official Kubernetes docs will familiarize you with Kubernetes using [minikube]. It's part of the official Kubernetes documentation, so it will likely stay pretty up-to-date, and doesn't stray too far into any opinionated stance on infrastructure.
- Also in the official documentation, the _[kubectl Cheat Sheet]_ is a useful guide for the things you'll find yourself doing most often with Kubernetes.
- DigitalOcean [publishes several high-quality e-book series](https://www.digitalocean.com/community/curriculums/kubernetes-for-full-stack-developers) for learning how to use and administer Kubernetes clusters, with series for both a platform operator's and an application developer's perspective.
- [Kelsey Hightower], a developer advocate for Google Cloud, maintains of the most popular Kubernetes learning guides, _[Kubernetes The Hard Way]_. It emphasizes learning all of the individual aspects of Kubernetes rather than getting started quickly.


[The Illustrated Children's Guide to Kubernetes]: https://www.cncf.io/the-childrens-illustrated-guide-to-kubernetes/
[Phippy Goes to the Zoo]: https://www.cncf.io/phippy-goes-to-the-zoo-book/
[Cloud Native Computing Foundation]: https://www.cncf.io/
[Learn Kubernetes Basics]: https://kubernetes.io/docs/tutorials/kubernetes-basics/
[kubectl Cheat Sheet]: https://kubernetes.io/docs/reference/kubectl/cheatsheet/
[Kelsey Hightower]: https://twitter.com/kelseyhightower
[Kubernetes The Hard Way]: https://github.com/kelseyhightower/kubernetes-the-hard-way


## Copyright

[![Creative Commons BY-NC-SA 4.0](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)][license]

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][license].

[license]: http://creativecommons.org/licenses/by-nc-sa/4.0/
