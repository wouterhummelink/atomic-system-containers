FROM kubernetes-node
MAINTAINER "Jason Brooks" <jbrooks@redhat.com>

ENV container=docker

ENV NAME=kubernetes-proxy VERSION=0 RELEASE=8 ARCH=x86_64
LABEL bzcomponent="$NAME" \
        name="$FGC/$NAME" \
        version="$VERSION" \
        release="$RELEASE.$DISTTAG" \
        architecture="$ARCH" \
        atomic.type='system'

RUN dnf install -y iptables conntrack-tools kube-proxy && dnf clean all

LABEL RUN /usr/bin/docker run -d --privileged --net=host 

COPY launch.sh /usr/bin/kube-proxy-docker.sh

COPY service.template config.json.template /exports/

RUN mkdir -p /exports/hostfs/etc/kubernetes && 
COPY config proxy  /exports/hostfs/etc/kubernetes/

ENTRYPOINT ["/usr/bin/kube-proxy-docker.sh"]

