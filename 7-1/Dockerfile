FROM centos/php-71-centos7

USER 0

# Install custom packages
RUN INSTALL_PKGS="http://centos.netzmarkt.de/7/sclo/x86_64/sclo/sclo-php71/sclo-php71-php-pecl-imagick-3.4.4-1.el7.x86_64.rpm http://centos.netzmarkt.de/7/sclo/x86_64/sclo/sclo-php71/sclo-php71-php-pecl-ssh2-1.1.2-2.el7.x86_64.rpm rh-nodejs10" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS --nogpgcheck && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

USER 1001
