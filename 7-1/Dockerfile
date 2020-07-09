FROM centos/php-71-centos7

USER 0

# Use CentOS archive repos (vault.centos.org)
RUN RELEASE=$(awk '{print $4}' /etc/centos-release) && \
    for REPO in os updates extras; \
    do \
      sed -i -e "s/^#[[:space:]]*baseurl=[[:print:]]*\/${REPO}\/[[:print:]]*/baseurl=http:\/\/vault.centos.org\/centos\/${RELEASE}\/${REPO}\/\$basearch\//" -e "s/^\(mirrorlist=[[:print:]]*\&repo=${REPO}\&[[:print:]]*\)/#\1/" /etc/yum.repos.d/CentOS-Base.repo; \
    done && \
    sed -i -e "s/^#[[:space:]]*baseurl=[[:print:]]*mirror.centos.org[[:print:]]*\/sclo\/[[:print:]]*/baseurl=http:\/\/vault.centos.org\/centos\/${RELEASE}\/sclo\/\$basearch\/sclo\//" -e "s/^\(mirrorlist=[[:print:]]*\&repo=sclo-sclo[[:print:]]*\)/#\1/" /etc/yum.repos.d/CentOS-SCLo-scl.repo && \
    yum clean all -y

# Install custom packages
RUN INSTALL_PKGS="sclo-php71-php-pecl-imagick sclo-php71-php-pecl-ssh2 rh-nodejs10" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS --nogpgcheck && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

USER 1001
