load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
)
load("@envoy_api//bazel:api_build_system.bzl", "api_proto_package")

package(default_visibility = ["//visibility:public"])

api_proto_package()
envoy_cc_library(
    name = "appnet_filter_lib",
    srcs = ["appnet_filter.cc", "thirdparty/base64.cpp"],
    hdrs = ["appnet_filter.h", "thirdparty/json.hpp", "thirdparty/base64.h"],
    repository = "@envoy",
    deps = [
        ":pkg_cc_proto",
        "@envoy//source/extensions/filters/http/common:pass_through_filter_lib",
        "@envoy//source/common/http:utility_lib",
    ],
)

envoy_cc_library(
    name = "appnet_filter_config",
    srcs = ["appnet_filter_config.cc"],
    repository = "@envoy",
    deps = [
        ":appnet_filter_lib",
        "@envoy//envoy/server:filter_config_interface",
    ],
)