FROM node:14-alpine

ARG GIT_USER
ARG GIT_EMAIL

RUN \
    apk add --no-cache \
        bash \
        git \
    && \
    npm install -g \
        @angular/cli \
        typescript \
    && \
    if [ -n "${GIT_EMAIL}" ]; then git config --global user.email "${GIT_EMAIL}"; fi \
    && \
    if [ -n "${GIT_USER}" ]; then git config --global user.name "${GIT_USER}"; fi


EXPOSE 4200

CMD [ "tail", "-f", "/dev/fd/2" ]
