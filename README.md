# yannoff/ng

A node docker image with Angular.

## Usage

### Dynamic build

#### Build arguments

Name|Description
---|---
`GIT_USER`|Optional value to be stored as `user.name` global config
`GIT_EMAIL`|Optional value to be stored as `user.email` global config

#### Example

_Dynamic builds allow for flexible images._

```yaml
# docker-compose.yaml
version: '3.6'
services:
    ng:
        build:
            context: https://github.com/yannoff/docker-ng.git#:14
            args:
                GIT_USER: acme
                GIT_EMAIL: acme@example.com

        volumes:
            - ./:/src

        working_dir: /src

        ports:
            - 4200:4200

        # Here we launch the Angular Live Development Server
        # as the main container command
        # Beware that in order to be accessible from the host
        # machine, the server must listen to 0.0.0.0 instead
        # of the default "localhost" binding
        command:
            - ng
            - serve
            - --host
            - 0.0.0.0
            - --verbose
            - --watch
```

### Compiled image

_Compiled images are convenient to run one-shot commands, such as creating a brand new project._

#### Supported tags

- [yannoff/ng:16](https://github.com/yannoff/docker-ng/tree/master/14/Dockerfile) Based on [node:16-alpine](https://github.com/nodejs/docker-node/blob/b36041b26d8423f1838fb8232411a12f882cbb6a/16/alpine3.15/Dockerfile).
- [yannoff/ng:14](https://github.com/yannoff/docker-ng/tree/master/14/Dockerfile) Based on [node:14-alpine](https://github.com/nodejs/docker-node/blob/b36041b26d8423f1838fb8232411a12f882cbb6a/14/alpine3.15/Dockerfile).
- [yannoff/ng:12](https://github.com/yannoff/docker-ng/tree/master/14/Dockerfile) Based on [node:12-alpine](https://github.com/nodejs/docker-node/blob/b36041b26d8423f1838fb8232411a12f882cbb6a/12/alpine3.15/Dockerfile).


#### Example

```
docker run -it --rm -u $UID:$GID -v $PWD:/src -w /src yannoff/ng ng new hello-world
```

## License

Licensed under the [MIT License](LICENSE).
