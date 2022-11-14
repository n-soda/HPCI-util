#FROM centos:8
FROM quay.io/centos/centos:stream8

RUN set -x && \
	yum -y install wget openssl epel-release && \
	yum -y install myproxy gsissh-clients && \
	mkdir -p /etc/grid-security/certificates && \
	mkdir -p ~root/.ssh && \
	echo 'ServerAliveInterval 30' > ~root/.ssh/config && \
	rm -rf /var/cache/yum/* && \
	yum clean all && \
	rm -f /tmp/ks-script-* /tmp/yum.log

COPY ./hpci-cert-update /usr/local/bin/

CMD [ "sh", "-c", "/usr/local/bin/hpci-cert-update && /bin/bash" ]
