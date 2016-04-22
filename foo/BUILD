load("@bazel_tools//tools/build_defs/docker:docker.bzl", "docker_build")

docker_build(
  name = "mydocker",
  tars = ["alpine.tar"],
  files = ["//:myfile"],
)
