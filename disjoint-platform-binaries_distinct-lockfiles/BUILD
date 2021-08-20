python_requirement_library(name="psutil", requirements=["psutil"])

pex_binary(
    name="psutil_linux",
    entry_point="<none>",
    dependencies=[":psutil"],
    platforms=["linux-cp37"],
    resolve="psutil_linux_lock.txt",
)

pex_binary(
    name="psutil_macos",
    entry_point="<none>",
    dependencies=[":psutil"],
    platforms=["macos-cp37"],
    resolve="psutil_macos_lock.txt",
)
