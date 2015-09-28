Buildpack for ffmpeg
====================

This project is a Scalingo [buildpack](http://doc.scalingo.com/buildpacks) for using [ffmpeg](http://www.ffmpeg.org/) in your project.

It doesn't do anything else, you have to use it alongside another buildpack thanks to the [mutli-buildpack](https://github.com/Scalingo/multi-buildpack).

This buildpack provides a static build of the 2.8 version of FFMPEG downloaded from https://www.ffmpeg.org/download.html

Usage
-----

## Setup the multi-buildpack
To use this buildpack, you should prepare .buildpacks file that contains this buildpack url and your real buildpack url.  

```
$ cat .buildpacks
https://github.com/Scalingo/ffmpeg-buildpack.git
https://github.com/Scalingo/go-buildpack.git 
```

The first buildpack will install FFMPEG, the second will handle the deployment of your go application. For any other technology,
go to [http://doc.scalingo.com/buildpacks/](http://doc.scalingo.com/buildpacks/)

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
