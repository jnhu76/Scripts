Run the following commands as root or user with sudo access to update the packages list and install the prerequisites:
To install the Development Tools packages, run the following command as root or user with sudo privileges :
```
$ sudo apt update
$ sudo apt-get upgrade -y
$ sudo apt-get dist-upgrade -y
$ sudo apt-get install build-essential software-properties-common manpages-dev -y
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
$ sudo apt-get update -y
```

Verify that the GCC compiler is successfully installed by running the following command that prints the GCC version:

```
$ gcc --version
gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

Installing Multiple GCC Versions

```
$ sudo apt install gcc-8 g++-8 gcc-9 g++-9 gcc-10 g++-10 gcc-11 g++-11 -y
```
change the default version

```
$ ls -larth `which gcc`*
lrwxrwxrwx 1 root root 23 Thg 1  4  2019 /usr/bin/gcc-7 -> aarch64-linux-gnu-gcc-7
lrwxrwxrwx 1 root root 23 Thg 3 10  2020 /usr/bin/gcc-8 -> aarch64-linux-gnu-gcc-8
lrwxrwxrwx 1 root root 23 Thg 4 23  2020 /usr/bin/gcc-9 -> aarch64-linux-gnu-gcc-9
lrwxrwxrwx 1 root root 24 Thg 4 15 19:21 /usr/bin/gcc-10 -> aarch64-linux-gnu-gcc-10
lrwxrwxrwx 1 root root 24 Thg 4 29 01:05 /usr/bin/gcc-11 -> aarch64-linux-gnu-gcc-11
lrwxrwxrwx 1 root root 21 Thg 5 27 09:22 /usr/bin/gcc -> /etc/alternatives/gcc
```

```
$ ls -larth `which g++`*
lrwxrwxrwx 1 root root 23 Thg 1  4  2019 /usr/bin/g++-7 -> aarch64-linux-gnu-g++-7
lrwxrwxrwx 1 root root 23 Thg 3 10  2020 /usr/bin/g++-8 -> aarch64-linux-gnu-g++-8
lrwxrwxrwx 1 root root 23 Thg 4 23  2020 /usr/bin/g++-9 -> aarch64-linux-gnu-g++-9
lrwxrwxrwx 1 root root 24 Thg 4 15 19:21 /usr/bin/g++-10 -> aarch64-linux-gnu-g++-10
lrwxrwxrwx 1 root root 24 Thg 4 29 01:05 /usr/bin/g++-11 -> aarch64-linux-gnu-g++-11
lrwxrwxrwx 1 root root 21 Thg 5 27 09:22 /usr/bin/g++ -> /etc/alternatives/g++
```

So we have 5 - use these in update-alernatives

```
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 7 --slave /usr/bin/g++ g++ /usr/bin/g++-7 --slave /usr/bin/gcov gcov /usr/bin/gcov-7
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 8 --slave /usr/bin/g++ g++ /usr/bin/g++-8 --slave /usr/bin/gcov gcov /usr/bin/gcov-8
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 9 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 10 --slave /usr/bin/g++ g++ /usr/bin/g++-10 --slave /usr/bin/gcov gcov /usr/bin/gcov-10
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11

$ sudo update-alternatives --config gcc
There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc-11   11        auto mode
  1            /usr/bin/gcc-10   10        manual mode
  2            /usr/bin/gcc-11   11        manual mode
  3            /usr/bin/gcc-7    7         manual mode
* 4            /usr/bin/gcc-8    8         manual mode
  5            /usr/bin/gcc-9    9         manual mode

Press <enter> to keep the current choice[*], or type selection number:

```
Done

```
$ gcc --version
gcc (Ubuntu/Linaro 8.4.0-1ubuntu1~18.04) 8.4.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
$ g++ --version
g++ (Ubuntu/Linaro 8.4.0-1ubuntu1~18.04) 8.4.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```