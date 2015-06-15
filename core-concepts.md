---
layout: default
permalink: /core-concepts/
title: Core Concepts
---

# Core Concepts

In order to better understand how and why Flysystem works
the way it does, several concepts require some explenation.

## Overview

* [Adapters](#adapters)
* [Relative Paths](#relative-paths)
* [Files first](#files-first)

## Adapters

The main entry point for the fielsystem API is the
FilesystemInterface. When working with Filesystems, this is
the class you'll want to be talking to.

The reason why Flysystem works, it because of it's use of the
adapter pattern. The inconsistencies of the different
filesystems are elimintated in these adapters.

While adapters have a public interface (publically accessible
methods), they should be considered __internal__.

## Relative Paths

Portability is a very important concept within Flysystem. In order
to role out this aspect to the fullest all paths in flysystem are
relative. Filesystem root paths, wether remote or local, are viewed
as endpoints. Because of this, filesystems are moveable independantly.
This allows parts of the application file handling to move to other
storage types, while the majority is in a centralized location.

Like the storage type, root paths are an implementation detail. When
root paths are defined as configuration, the stability of your code
improves.

## Files First

Flysystem has a files first approach. Storage systems like AWS S3
are linear filesystems, this means the path to a file is used as an
identifier, rather than a representation of all the directories it's
nested in.

This means directories are second class citezens. Because of this
directories will be automatically be created on filesystems that require
them when writing files. Not only does this make handing writes a lot
easier, it also ensures a consistent behavious across all filesystem 
types.