FROM bitnami/minideb-extras:jessie-r13

MAINTAINER Bitnami <containers@bitnami.com>

ENV BITNAMI_APP_NAME=phpmyadmin \
    BITNAMI_IMAGE_VERSION=4.6.6-r2 \
    PATH=/opt/bitnami/php/bin:$PATH

# System packages required
RUN install_packages libssl1.0.0 libaprutil1 libapr1 libc6 libuuid1 libexpat1 libpcre3 libldap-2.4-2 libsasl2-2 libgnutls-deb0-28 zlib1g libp11-kit0 libtasn1-6 libnettle4 libhogweed2 libgmp10 libffi6 libxslt1.1 libtidy-0.99-0 libreadline6 libncurses5 libtinfo5 libsybdb5 libmcrypt4 libstdc++6 libpng12-0 libjpeg62-turbo libbz2-1.0 libxml2 libcurl3 libfreetype6 libicu52 libgcc1 libgcrypt20 libgssapi-krb5-2 liblzma5 libidn11 librtmp1 libssh2-1 libkrb5-3 libk5crypto3 libcomerr2 libgpg-error0 libkrb5support0 libkeyutils1

# Additional modules required
RUN bitnami-pkg unpack apache-2.4.25-0 --checksum 8b46af7d737772d7d301da8b30a2770b7e549674e33b8a5b07480f53c39f5c3f
RUN bitnami-pkg install libphp-5.6.30-0 --checksum b9689caaab61862444c97756b1a9bf575731c4d0e71aa962d58518a231b33155
RUN bitnami-pkg unpack php-5.6.30-1 --checksum 96835743d668832c0b8464711587e5339969a96cafa1b319ca058697efd2857c

# Install phpmyadmin
RUN bitnami-pkg unpack phpmyadmin-4.6.6-0 --checksum 66fa6e4367448b7256b8f86900217c914116d42cd6fd5452a3a60aa66c978fc1

COPY rootfs /

ENV APACHE_HTTP_PORT="80" \
    APACHE_HTTPS_PORT="443" \
    REQUIRE_LOCAL="0" \
    DATABASE_HOST="mariadb" \
    DATABASE_PORT="3306"

VOLUME ["/bitnami/apache", "/bitnami/php", "/bitnami/phpmyadmin"]

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]

CMD ["nami","start","--foreground","apache"]
