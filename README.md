# bazel_docker_bug_reproduction

Demonstrate what seems like a bazel bug with docker

```
bazel run //foo:mydocker

% docker run -it bazel/foo:mydocker sh -c 'ls -l'
total 52
drwxr-xr-x    2 root     root          4096 Jan  1  1970 bin
drwxr-xr-x    5 root     root           380 Apr 22 17:53 dev
drwxr-xr-x   15 root     root          4096 Apr 22 17:53 etc
drwxr-xr-x    2 root     root          4096 Jan  1  1970 home
drwxr-xr-x    6 root     root          4096 Jan  1  1970 lib
lrwxrwxrwx    1 root     root            12 Jan  1  1970 linuxrc -> /bin/busybox
drwxr-xr-x    5 root     root          4096 Jan  1  1970 media
drwxr-xr-x    2 root     root          4096 Jan  1  1970 mnt
dr-xr-xr-x  158 root     root             0 Apr 22 17:53 proc
drwx------    2 root     root          4096 Jan  1  1970 root
drwxr-xr-x    2 root     root          4096 Jan  1  1970 run
drwxr-xr-x    2 root     root          4096 Jan  1  1970 sbin
dr-xr-xr-x   13 root     root             0 Apr 22 17:53 sys
-r-xr-xr-x    1 root     root             6 Jan  1  1970 t
drwxrwxrwt    2 root     root          4096 Jan  1  1970 tmp
drwxr-xr-x    7 root     root          4096 Jan  1  1970 usr
drwxr-xr-x    9 root     root          4096 Jan  1  1970 var
```

As you can see, the file shows up with the name `t` instead of `revision.txt`.

It seems like the filename inside the container is always the last letter of the filename in the outs.

```
% bazel version
Build label: 0.2.0
Build target: bazel-out/local_linux-fastbuild/bin/src/main/java/com/google/devtools/build/lib/bazel/BazelServer_deploy.jar
Build time: Tue Feb 23 13:08:29 2016 (1456232909)
Build timestamp: 1456232909
Build timestamp as int: 1456232909
```
