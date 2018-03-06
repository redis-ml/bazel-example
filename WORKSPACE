
# We use 'pubref' proto libraries, which already wraps com_google_protobuf.
# # Prefer 'http_archive' to 'git_repository'.
# http_archive(
#     name = "com_google_protobuf",
#     sha256 = "cef7f1b5a7c5fba672bec2a319246e8feba471f04dcebfe362d55930ee7c1c30",
#     strip_prefix = "protobuf-3.5.0",
#     urls = ["https://github.com/google/protobuf/archive/v3.5.0.zip"],
# )

git_repository(
  name = "org_pubref_rules_protobuf",
  remote = "https://github.com/pubref/rules_protobuf",
  tag = "v0.8.1",
  #commit = "..." # alternatively, use latest commit on master
)

load("@org_pubref_rules_protobuf//python:rules.bzl", "py_proto_repositories")
py_proto_repositories()

# Add other protobuf output languages here.
# ...

#####################
# Enable Python pip
# 1-A. Pull down rules_python
git_repository(
    name = "io_bazel_rules_python",
    remote = "https://github.com/bazelbuild/rules_python.git",
    commit = "c55f779479aee4a3c5f197ecc42bc62af3012b16",
)

# 1-B. Load the skylark file containing the needed functions
load("@io_bazel_rules_python//python:pip.bzl", "pip_repositories", "pip_import")

# 1-C. Invoke pip_repositories to load rules_python internal dependencies
pip_repositories()

# 1-D. Invoke pip_import with the necessary python requirements.  You can refer to the
# one in rules_protobuf, or roll your own (make sure it includes 'grpcio==1.6.0' (or later)).
pip_import(
   name = "pip_grpcio",
   requirements = "@org_pubref_rules_protobuf//python:requirements.txt",
)

# 1-E. Load the requirements.bzl file that will be written in this new workspace
# defined in 1-D.
load("@pip_grpcio//:requirements.bzl", pip_grpcio_install = "pip_install")
pip_grpcio_install()

# Install our own pip packages.
pip_import(
    name = "pip_testdata_run",
    requirements = "//testdata/py:run-requirements.txt"
)

load("@pip_testdata_run//:requirements.bzl", pip_testdata_run_install = "pip_install")
pip_testdata_run_install()
