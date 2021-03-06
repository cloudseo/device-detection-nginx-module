# Nginx Device Detection Module

### Note

This module is highly experimental. Please use with caution!


## Compilation

### Prerequisites

To be able to compile this module you need [libyaml](http://pyyaml.org/wiki/LibYAML)
available.

It should be registered with ldconfig to be usable:

    ldconfig -p | grep "libyaml"

During compilation the following header files have to be available:

- yaml.h

### Unit Test Requirements

The unit tests use [Test::Nginx](http://github.com/agentzh/test-nginx) and Lua.

To be able to run them using `prove` you need to compile nginx with the
[lua module](https://github.com/openresty/lua-nginx-module).

### Nginx

Using this module is as easy as recompiling nginx from source:

```shell
cd /path/to/nginx/src
./configure --add-module=/path/to/device-detection-nginx-module
make install
```

Or if you want to have debug logs available:

```shell
cd /path/to/nginx/src
./configure --add-module=/path/to/device-detection-nginx-module --with-debug
make install
```

To be able to run the unit tests you need additional modules configured:

```shell
cd /path/to/nginx/src
./configure \
  --add-module=/projects/public/lua-nginx-module \
  --add-module=/projects/private/device-detection-nginx-module
make install
```


## Lint

The included Makefile includes a lint-target to check the code against the
[Google C++ Style Guide](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml).

For a valid link to cpplint please refer to the style guide.

If "cpplint" is available in your path with the (exact) name of "cpplint" you
can run "make lint" to automatically lint all source files.


## Attributions

The _devices.yml_ used is an excerpt taken from the
[Piwik DeviceDetector](https://github.com/piwik/device-detector)
project. See there for detailed license information about the data contained.
