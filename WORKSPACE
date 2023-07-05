workspace(
    name = "semantic-mediawiki",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Docker rules
http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "1f4e59843b61981a96835dc4ac377ad4da9f8c334ebe5e0bb3f58f80c09735f4",
    strip_prefix = "rules_docker-0.19.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.19.0/rules_docker-v0.19.0.tar.gz"],
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

load("@io_bazel_rules_docker//container:container.bzl", "container_pull")

# Pull MediaWiki base container.
# NOTE: This must be pinned to a particular release to satisfy Semantic MediaWiki compatibility, see:
# https://www.semantic-mediawiki.org/wiki/Help:Compatibility

container_pull(
    name = "mediawiki-linux-amd64",
    digest = "sha256:331a8c35a19830862e4a84e924fa5830d9ce41b4ae671d9cd2f0c16307d4b31b",  # mediawiki:1.37.1, linux/amd64
    registry = "index.docker.io",
    repository = "library/mediawiki",
)
