FROM httpd:2.4-alpine

ENV TZ=${TZ:-UTC}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV APP_ROOT=/var/www/app
ENV SERVER_NAME=localhost
ENV DOCUMENT_ROOT=${APP_ROOT}/public_html
ENV APACHE_LOG_DIR=${APP_ROOT}/docker/apache/logs
ENV APACHE_RUN_GROUP=www-data
ENV APACHE_RUN_USER=www-data

RUN apk add --update --no-cache tzdata

WORKDIR ${APP_ROOT}

RUN sudo mkdir -p ${DOCUMENT_ROOT}
RUN sudo mkdir -p ${DOCUMENT_ROOT}/public_html
RUN sudo mkdir -p ${APACHE_LOG_DIR}
RUN sudo touch ${APACHE_LOG_DIR}/access.log
RUN sudo touch ${APACHE_LOG_DIR}/error.log
RUN chown -R ${APACHE_RUN_USER}:${APACHE_RUN_USER} ${DOCUMENT_ROOT}

RUN ln -s ${APP_ROOT}/public_html/index.php ${DOCUMENT_ROOT}

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
