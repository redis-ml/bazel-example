package(default_visibility = ["//visibility:public"])

#py_library(
#    name = "lib",
#    srcs = ["lib.py"],
#)

py_binary(
    name = "run-proto",
    srcs = ["run-proto.py"],
    deps = [
        ":lib",
        "//proto/serices:api_service_py_proto"
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
        "server.py",
    ],
    deps = [
        ":lib", # a py_proto_library rule
        "//proto/serices:api_service_py_proto"
        requirement("boto3"),
    ],
)
