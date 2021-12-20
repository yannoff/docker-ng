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
            context: https://github.com/yannoff/docker-ng#:14
            args:
                GIT_USER: acme
                GIT_EMAIL: acme@example.com
        volumes:
            - ./:/src
        working_dir: /src
        ports:
            - 4200:4200
```

### Compiled image

_Compiled images are convenient to run one-shot commands, such as creating a brand new project._

#### Example

```
docker run -it --rm -u $UID:$GID -v $PWD:/src -w /src yannoff/ng ng new hello-world
```

## License

Licensed under the [MIT License](LICENSE).
