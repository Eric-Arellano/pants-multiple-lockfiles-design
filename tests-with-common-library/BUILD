python_requirement_library(name="colors", requirements=["ansicolors>=1,<2"])
python_requirement_library(name="django2", requirements=["django==2"])
python_requirement_library(name="django3", requirements=["django==3"])

python_library(name="lib", requirements=[":colors"])

python_tests(
    name="test_django2",
    sources=["test_django2.py"],
    dependencies=[":lib", ":django2"],
    resolve="django2_lock.txt",
)

python_tests(
    name="test_django3",
    sources=["test_django3.py"],
    dependencies=[":lib", ":django3"],
    resolve="django3_lock.txt",
)
