FROM centos/php-71-centos7

USER 0

# Install custom packages
RUN INSTALL_PKGS="sclo-php71-php-pecl-imagick rh-nodejs10" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS --nogpgcheck && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

USER 1001
