ARG NV=14

FROM node:${NV}-alpine

ARG GIT_USER
ARG GIT_EMAIL

RUN \
    apk add --no-cache \
        bash \
        git \
        vim \
    && \
    npm install -g \
        @angular/cli \
        typescript \
        typings \
    && \
    if [ -n "${GIT_EMAIL}" ]; then git config --global user.email "${GIT_EMAIL}"; fi \
    && \
    if [ -n "${GIT_USER}" ]; then git config --global user.name "${GIT_USER}"; fi \
    && \
    { \
        cd /usr/share/vim/*/syntax && wget https://raw.githubusercontent.com/leafgarland/typescript-vim/master/syntax/typescript.vim \
        && \
        echo 'au BufNewFile,BufReadPost *.ts          setf typescript' >> /usr/share/vim/*/filetype.vim || true; \
    }

EXPOSE 4200

CMD [ "tail", "-f", "/dev/fd/2" ]
