mkpack
======

MaKe PACKage in one musical note

### How it works

* mkdeb
	* read control file to parse package name, package version and architecture.
	* auto detect installation scripts (postinst, postrm, preinst, prerm), control file and conffile
	* auto detect data file structure

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
