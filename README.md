mkpack
======

MaKe PACKage in one musical note

### Requirement

It require pre-installed these tools:
	* coreutils (md5sum, dirname)
	* binutils (ar)
	* sed
	* awk

### Features

* mkdeb - make package .deb for debian/ubuntu and any debian-based

### Usage

```bash
	mkdeb path_to_project

	Example:
		mkdeb /home/wikilinux/deb/mkpack
```

### Example

* Create .deb package

```bash
	[root@lab1.wikilinux.vn:~]# cd mkpack/
	[root@lab1.wikilinux.vn:~/mkpack]# ls
	example  mkdeb  README.md
	[root@lab1.wikilinux.vn:~/mkpack]# ls example/mkpack/
	control  postinst  usr
	[root@lab1.wikilinux.vn:~/mkpack]# ./mkdeb example/mkpack/
	Package is created at example/mkpack_0.9-1_all.deb
```

* Check and install package

```bash
	[root@lab1.wikilinux.vn:~/mkpack]# dpkg --info example/mkpack_0.9-1_all.deb
	 new debian package, version 2.0.
	 size 2298 bytes: control archive= 698 bytes.
	     260 bytes,     9 lines      control
	     148 bytes,     3 lines      md5sums
	      60 bytes,     3 lines   *  postinst             #!/bin/bash
	 Package: mkpack
	 Version: 0.9-1
	 Architecture: all
	 Maintainer: Xuta Le <xuta.le@wikilinux.vn>
	 Depends: coreutils, binutils, sed, mawk | gawk
	 Section: devel
	 Priority: standard
	 Description: mkpack - MaKe PACKage in one musical note
	  Home page: http://wikilinux.vn
	[root@lab1.wikilinux.vn:~/mkpack]# dpkg --contents example/mkpack_0.9-1_all.deb
	drwxr-xr-x root/root         0 2014-03-27 22:11 ./usr/
	drwxr-xr-x root/root         0 2014-03-27 22:11 ./usr/bin/
	-rwxr-xr-x root/root      2372 2014-03-27 22:11 ./usr/bin/mkdeb
	[root@lab1.wikilinux.vn:~/mkpack]# dpkg -i example/mkpack_0.9-1_all.deb
	Selecting previously deselected package mkpack.
	(Reading database ... 57489 files and directories currently installed.)
	Unpacking mkpack (from example/mkpack_0.9-1_all.deb) ...
	Setting up mkpack (0.9-1) ...
	Finish installation mkpack
	Enjoy.
	[root@lab1.wikilinux.vn:~/mkpack]# dpkg -l | grep mkpack
	ii  mkpack              0.9-1               mkpack - MaKe PACKage in one musical note
	[root@lab1.wikilinux.vn:~/mkpack]#
```
