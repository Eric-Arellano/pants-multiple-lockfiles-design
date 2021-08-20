python_requirement_library(name="django2", requirements=["django==2"])
python_requirement_library(name="django3", requirements=["django==3"])

python_tests(
    name="test_django2",
    sources=["test_django2.py"],
    dependencies=[":django2"],
    resolve="django2_lock.txt",
)

python_tests(
    name="test_django3",
    sources=["test_django3.py"],
    dependencies=[":django3"],
    resolve="django3_lock.txt",
)
