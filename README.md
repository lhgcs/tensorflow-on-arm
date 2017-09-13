# Tensorflow-on-arm

Inspired by the [tensorflow-on-raspberry-pi](https://github.com/samjabrahams/tensorflow-on-raspberry-pi).
This script applies patch in bazel (for supports aarch64) and changes eigen version for compile with neon support.

## Dependences
```shell
apt-get install openjdk-8-jdk automake autoconf
apt-get install curl zip unzip libtool swig zlib1g-dev pkg-config git zip g++ unzip wget

# For python2.7
apt-get install python-numpy python-dev python-pip
 
# For python3
apt-get install python3-numpy python3-dev python3-pip
```
## Building from Source
```shell
cd build_tensorflow/
```

## Cross-compilation
Make you sure added arm architecture, see how to adds in debian flavors:
```shell
dpkg --add-architecture armhf
echo "deb [arch=armhf] http://httpredir.debian.org/debian/ stretch main contrib non-free" >> /etc/apt/source.list
```
if you want compile python support:
```shell
# For python2.7
apt-get install libpython-all-dev:armhf

# For python3
apt-get install libpython3-all-dev:armhf
```

## Edit tweaks like bazel resources, board model, and others
see configuration file examples in: build_tensorflow/configs/

## Finally, compile tensorflow.
```shell
chmod +x build_tensorflow.sh
./build_tensorflow.sh <path-of-config>
# If no output errors, the pip package will be in the directory: /tmp/tensorflow_pkg/ 
```
