package(default_visibility = ["//visibility:public"])

load("@org_pubref_rules_protobuf//python:rules.bzl", "py_proto_library")


############
proto_library(
    name = "api_message_proto",
    srcs = [":api_message_protos"],
)

###########

filegroup(
    name = "api_message_protos",
    srcs = [
        "api_message.proto",
    ],
)

filegroup(
    name = "api_service_protos",
    srcs = [
        "api_service.proto",
    ],
)

py_proto_library(
    name = "py_message",
    protos = [":api_message_protos"],
    verbose = 0,
    with_grpc = False,
)

py_proto_library(
    name = "py_service",
    protos = [
        ":api_service_protos",
    ],
    proto_deps = [":py_message"],
    verbose = 0,
    with_grpc = True,
)
