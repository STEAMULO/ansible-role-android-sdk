# Ansible Role: Android SDK

[![Build Status](https://travis-ci.org/nickpack/ansible-role-android-sdk.svg?branch=master)](https://travis-ci.org/nickpack/ansible-role-android-sdk)

An Ansible Role that installs the Android SDK tools, SDK packages and dependencies on Ubuntu and RedHat based OS'.

## Requirements

A recent version of Ubuntu.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    android_sdk_download_location: http://dl.google.com/android/android-sdk_r23.0.2-linux.tgz

The location to the Android SDK tools package to be installed.

    android_sdk_install_location: /opt

The location on disk where you'd like to SDK to be installed.

    ubuntu_dependency_packages:
      - "libncurses5"
      - "libstdc++6"
      - "zlib1g"
      - "imagemagick"
      - "expect"
      - "gradle"
      - "ant"
      - "ccache"
      - "autoconf"
      - "automake"
      - "ant"
      - "ccache"
      - "python-dev"
      - "zlibc"

A list of aptitude installable build dependency packages.

    ubuntu_precise_dependency_packages:
      - "libgd2-xpm"
      - "libgphoto2-2"
      - "libsane"
      - "ia32-libs-multiarch"

A list of aptitude installable build dependencies for Ubuntu Precise.

    rh_dependency_packages:
      - expect
      - libstdc++.i686
      - mesa-libGL-devel
      - ncurses-libs.i686
      - zlib.i686

A list of yum installable build dependencies for RedHat based OS.

    android_sdk_update_path: true

Whether or not the role should update the PATH in /etc/environment with the relevant android SDK locations

    android_sdk_base_buildtools_version: 25.0.3

The main build tools version from the SDK to use, mainly useful for PATH updates.

    android_sdk_tools_to_install:
      - "build-tools;{{ android_sdk_base_buildtools_version }}"
      - platform-tools
      - extras;m2repository;com;android;support;constraint;constraint-layout-solver;1.0.2
      - extras;m2repository;com;android;support;constraint;constraint-layout;1.0.2
      - extras;android;m2repository
      - extras;google;m2repository
    android_sdks_to_install:
      - platforms;android-25
      - platforms;android-24
      - platforms;android-23
      - platforms;android-22
      - platforms;android-21
      - platforms;android-20
      - platforms;android-19
      - platforms;android-8

The actual Android SDK packages to install using the SDK manager.

## Example Playbook

    - hosts: appbuild
      vars_files:
        - vars/main.yml
      roles:
        - { role: nickpack.android-sdk }

## License

BSD

## Author Information

Steamulo - www.steamulo.com

Forked from [Nick Pack](https://github.com/nickpack).

## Contributors

* @rodrigdav - Fixed bare variables that broke 2.2 compatibility
* @halkeye - Seperated SDK tools, fixed 64bit environment
* @edunham - Fixed 32bit support
* @peterjanes - Added RedHat family support
* @conorsch - Changed conditionals to allow > 14.04 support
