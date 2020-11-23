[![apupier](https://circleci.com/gh/apupier/minikube-on-circleci-example.svg?style=svg)](https://circleci.com/gh/apupier/minikube-on-circleci-example)

# Minikube on Circle CI example

Configuring Minikube on Circle CI is simple... when you know the tricks!
This repository is providing an example.

# Insights on the tricks

The main one is that you cannot use the docker build type! Minikube requires privileged docker which is not provided by Circle CI in this configuration. An `image` must be used.

The recent versions of Minikube introduced the `vm-driver` type `docker` which simplifies configuration.

The [minikube orb](https://circleci.com/developer/orbs/orb/ccpgames/minikube) is not working with recent versions (at least with my little tests).

# Other ways to have Kubernetes

If the requirement is to have a Kubernetes instance, not necessarily provided by minikube. I recommend having a look to the [kubernetes orb](https://circleci.com/developer/orbs/orb/circleci/kubernetes) or [microk8s](https://ubuntu.com/tutorials/install-a-local-kubernetes-with-microk8s#1-overview) as the vm provided by Circle CI is Ubuntu and it was also [suggested by a Circle CI employee](https://discuss.circleci.com/t/how-to-setup-minikube-for-testing/38134/5?u=apupier).
