---
id: testing-unit-py
title: Testing Unit Py
desc: ''
updated: 1617203999592
created: 1617203999592
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# Unit Testing Pulumi programs in Python

An example of writing mock-based unit tests with both infrastructure definition and tests written in Python. The example uses the [unittest](https://docs.python.org/3/library/unittest.html) test framework to define and run the tests.

## Running the tests

1. Create a Python virtualenv, activate it, and install dependencies:

   ```bash
   $ python3 -m venv venv
   $ source venv/bin/activate
   $ pip3 install -r requirements.txt
   ```

2. Run the tests:

   ```
   $ python -m unittest

   ------------------------------------------------------------
   Ran 2 tests in 0.004s

   OK
   ```

## Further steps

Learn more about testing Pulumi programs:

- [Testing Guide](https://www.pulumi.com/docs/guides/testing/)
- [Unit Testing Guide](https://www.pulumi.com/docs/guides/testing/unit/)

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [**main**.py](/assets/__main__.py)
- [infra.py](/assets/infra.py)
- [requirements.txt](/assets/requirements.txt)
- [test_ec2.py](/assets/test_ec2.py)

