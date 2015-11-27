FROM ubuntu:14.04
MAINTAINER Aleksej Gavrilov <le9i0nx@gmail.com>
RUN DEBIAN_FRONTEND=noninteractive \
    apt-get update  && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
        sudo openssh-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*  /tmp/*

ADD test/dockerfile/init-fake.conf /etc/init/fake-container-events.conf
RUN rm /usr/sbin/policy-rc.d; \
    rm /sbin/initctl; dpkg-divert --rename --remove /sbin/initctl
RUN locale-gen en_US.UTF-8 && update-locale LANG=en_US.UTF-8
RUN /usr/sbin/update-rc.d -f ondemand remove; \
    for f in \
        /etc/init/u*.conf \
        /etc/init/mounted-dev.conf \
        /etc/init/mounted-proc.conf \
        /etc/init/mounted-run.conf \
        /etc/init/mounted-tmp.conf \
        /etc/init/mounted-var.conf \
        /etc/init/hostname.conf \
        /etc/init/networking.conf \
        /etc/init/tty*.conf \
        /etc/init/plymouth*.conf \
        /etc/init/hwclock*.conf \
        /etc/init/module*.conf\
    ; do \
        dpkg-divert --local --rename --add "$f"; \
    done; \
    echo '# /lib/init/fstab: cleared out for bare-bones Docker' > /lib/init/fstab

RUN sed -ri 's/^session\s+required\s+pam_loginuid.so$/session optional pam_loginuid.so/' /etc/pam.d/sshd
RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN echo "root:000000" | chpasswd

ENV container docker
CMD ["/sbin/init"]



# docker run -d -it test-ubuntu14


