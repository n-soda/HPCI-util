#FROM centos:8
FROM quay.io/centos/centos:stream8

RUN set -x && \
	yum -y install wget openssl epel-release && \
	yum -y install myproxy gsissh-clients && \
	mkdir -p /etc/grid-security/certificates && \
	cd /etc/grid-security/certificates && \
	wget https://www.hpci.nii.ac.jp/ca/hpcica.pem && \
	wget https://www.hpci.nii.ac.jp/ca/61cd35bd.signing_policy && \
	wget https://www.hpci.nii.ac.jp/ca/hpcica.crl && \
	ln -s hpcica.pem `openssl x509 -in hpcica.pem -noout -hash`.0 && \
	ln -s hpcica.crl `openssl x509 -in hpcica.pem -noout -hash`.r0 && \
	mkdir -p ~root/.ssh && \
	echo 'ServerAliveInterval 30' > ~root/.ssh/config && \
	rm -rf /var/cache/yum/* && \
	yum clean all && \
	rm -f /tmp/ks-script-* /tmp/yum.log
