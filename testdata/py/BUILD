package(default_visibility = ["//visibility:public"])

py_library(
    name = "lib",
    srcs = ["lib.py"],
)

py_binary(
    name = "run-proto",
    srcs = ["run-proto.py"],
    deps = [
        ":lib",
        "//proto/services:py_message",
        "//proto/services:py_service",
    ],
)

filegroup(
    name = "srcs",
    srcs = ["BUILD"] + glob(["**/*.py"]),
)


# Load the 'packages' function from the 'pip_grpcio' workspace
load("@pip_testdata_run//:requirements.bzl", "requirement")

# Define a py_binary rule and include the grpcio package as a dependency.
py_binary(
    name = "my_grpc_server",
    srcs = [
        "my_grpc_server.py",
    ],
    deps = [
        ":lib", # a py_proto_library rule
        "//proto/services:py_message",
        "//proto/services:py_service",
        requirement("boto3"),
    ],
)
