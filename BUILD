package(default_visibility = ["//visibility:public"])

filegroup(
    name = "files",
    srcs = glob(
        ["**"],
        exclude = [
            "bazel-bin/**",
            "bazel-out/**",
            "bazel-stm32-rs/**",
            "bazel-testlogs/**",
        ],
    ),
    visibility = ["//visibility:public"],
)

exports_files(
    srcs = glob(["**"]) + [
        "Makefile",
    ],
    visibility = ["//visibility:public"],
)

genrule(
    name = "stm32g474_svd",
    srcs = [
        ":files",
        ":Makefile",
    ],
    outs = ["stm32g474.svd"],
    cmd_bash =
        "REPO_PATH=$$(dirname $(location Makefile)) && " +
        "source /home/tim/venv3/bin/activate && " +
        "rm -f $${REPO_PATH}/svd/stm32g474.svd.patched && " +
        "(cd $${REPO_PATH} && make -j8 svd/stm32g474.svd.patched) && " +
        "cp $${REPO_PATH}/svd/stm32g474.svd.patched $@",
    local = True,
)
