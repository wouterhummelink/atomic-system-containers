FROM registry.fedoraproject.org/fedora:26
MAINTAINER "Jason Brooks" <jbrooks@redhat.com>

ENV NAME=kubernetes-node VERSION=0 RELEASE=0 ARCH=x86_64
LABEL bzcomponent="$NAME" \
        name="$FGC/$NAME" \
        version="$VERSION" \
        release="$RELEASE.$DISTTAG" \
        architecture="$ARCH"

RUN dnf -y update && dnf clean all
ADD kubernetes.repo /etc/yum.repos.d/kubernetes.repo
RUN dnf install -y kubelet kubectl kubeadm kubernetes-cni findutils && dnf clean all
