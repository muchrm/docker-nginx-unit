FROM centos:7
ADD unit.repo /etc/yum.repos.d
RUN yum install -y unit \
    && yum clean all \
    && rm -rf /var/cache/yum
CMD ["unitd", "--no-daemon", "--control", "unix:/var/run/control.unit.sock"]