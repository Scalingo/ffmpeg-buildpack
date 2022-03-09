# [DEPRECATED] Buildpack: ffmpeg

The ffmpeg buildpack is deprecated. This is replaced with the use of the [APT buildpack](https://github.com/Scalingo/apt-buildpack/). Please refer to the [Scalingo documentation](https://doc.scalingo.com/platform/deployment/buildpacks/ffmpeg) for a more future proof way to install ffmpeg or ffprobe.

This project is a Scalingo [buildpack](http://doc.scalingo.com/buildpacks) for using [ffmpeg](https://www.ffmpeg.org) in your project.

It doesn't do anything else, you have to use it alongside another buildpack thanks to the [multi-buildpack](https://github.com/Scalingo/multi-buildpack).

This buildpack provides a static build of the 2.8 version of FFmpeg downloaded from https://www.ffmpeg.org/download.html

Usage
-----

## Setup the multi-buildpack
To use this buildpack, you should prepare .buildpacks file that contains this buildpack url and your real buildpack url.

```
$ cat .buildpacks
https://github.com/Scalingo/ffmpeg-buildpack.git
https://github.com/Scalingo/go-buildpack.git
```

The first buildpack will install FFmpeg, the second will handle the deployment of your go application. For any other technology,
go to [Scalingo documentation](https://doc.scalingo.com/platform/deployment/buildpacks/intro).

## Setup your application configuration

```
$ scalingo env-set BUILDPACK_URL=https://github.com/Scalingo/multi-buildpack.git
$ git push scalingo master
...
```

You can verify installing ffmpeg by following command.

```
$ scalingo run "ffmpeg -version"
```

## Need of ffprobe?

Define the following environment variable and we'll install the binary `ffprobe` alongside `ffmpeg`

```
WITH_FFPROBE=true
```

Do it through Scalingo's dashboard or with their command line tool:

```
scalingo env-set WITH_FFPROBE=true
```
