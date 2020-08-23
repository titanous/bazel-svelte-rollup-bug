workspace(name = "poc")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "e5d90f0ec952883d56747b7604e2a15ee36e288bb556c3d0ed33e818a4d971f2",
    strip_prefix = "bazel-skylib-1.0.2",
    urls = ["https://github.com/bazelbuild/bazel-skylib/archive/1.0.2.tar.gz"],
)

http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "10fffa29f687aa4d8eb6dfe8731ab5beb63811ab00981fc84a93899641fd4af1",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/2.0.3/rules_nodejs-2.0.3.tar.gz"],
)

http_archive(
    name = "build_bazel_rules_svelte",
    sha256 = "1304782be6b17962ad3f19d37310ca0674742a78ebb0aff37eb8e6b802ce340d",
    strip_prefix = "rules_svelte-0.16",
    urls = ["https://github.com/thelgevold/rules_svelte/archive/0.16.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories()

yarn_install(
    name = "npm",
    package_json = "@poc//:package.json",
    yarn_lock = "@poc//:yarn.lock",
)

load("@build_bazel_rules_svelte//:defs.bzl", "rules_svelte_dependencies")

rules_svelte_dependencies()

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()
