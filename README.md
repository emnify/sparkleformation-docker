# SparkleFormation in Docker

This container ([`emnify/sparkleformation`](https://hub.docker.com/r/emnify/sparkleformation/) allows to run [SparkleFormation](http://www.sparkleformation.io/) without having Ruby installed on the host.

## Usage

- The SparkleFormation project (with the `.sfn` config file) must be mounted to `/work`.
- Make sure that the `AWS_*` variables are exported prior to running the command.

```shell
$ docker run -it \
    -e AWS_REGION -e AWS_SECRET_ACCESS_KEY -e AWS_ACCESS_KEY_ID \
    -v ~/src/cloudformation/staging:/work \
    emnify/sparkleformation
```

Making above a shell alias allows to work as follows:


```shell
$ export AWS_REGION=...
$ alias sparkle="docker run -it -e AWS_REGION -e AWS_SECRET_ACCESS_KEY -e AWS_ACCESS_KEY_ID -v ~/src/cloudformation/staging:/work emnify/sparkleformation"
$ sparkle list
Name                                       Created                   Updated                   Status               Template Description
some-stack                                 2017-06-19 05:21:39 UTC   2017-09-21 08:34:44 UTC   UPDATE_COMPLETE      Some Example stack
```


