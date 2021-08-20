python_requirement_library(name="psutil", requirements=["psutil"])

pex_binary(
    name="psutil_linux",
    entry_point="<none>",
    dependencies=[":psutil"],
    platforms=["linux-cp37"],
    resolve="lock.txt",
)

pex_binary(
    name="psutil_macos",
    entry_point="<none>",
    dependencies=[":psutil"],
    platforms=["macos-cp37"],
    resolve="lock.txt",
)

pex_binary(
    name="psutil_cross-platform",
    entry_point="<none>",
    dependencies=[":psutil"],
    platforms=["linux-cp37", "macos-cp37"],
    resolve="lock.txt",
)
