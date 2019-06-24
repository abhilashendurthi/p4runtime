workspace(name = "com_github_p4lang_p4runtime")

load("//bazel:deps.bzl", "p4runtime_deps")
p4runtime_deps()

# Bazel rules for P4Runtime python library
load("@build_stack_rules_proto//python:deps.bzl", "python_grpc_library")
python_grpc_library()

load("@io_bazel_rules_python//python:pip.bzl", "pip_import", "pip_repositories")
pip_repositories()

pip_import(
    name = "protobuf_py_deps",
    requirements = "@build_stack_rules_proto//python/requirements:protobuf.txt",
)

load("@protobuf_py_deps//:requirements.bzl", protobuf_pip_install = "pip_install")
protobuf_pip_install()
pip_import(
    name = "grpc_py_deps",
    requirements = "@build_stack_rules_proto//python:requirements.txt",
)

load("@grpc_py_deps//:requirements.bzl", grpc_pip_install = "pip_install")
grpc_pip_install()

# Bazel rules for P4Runtime C++ library
load("@build_stack_rules_proto//cpp:deps.bzl", "cpp_proto_library")
cpp_proto_library()

load("@com_github_grpc_grpc//bazel:grpc_deps.bzl", "grpc_deps")
grpc_deps()

load("@com_google_googleapis//:repository_rules.bzl", "switched_rules_by_language")
switched_rules_by_language(
    name = "com_google_googleapis_imports",
    grpc = True,
    cc = True,
)