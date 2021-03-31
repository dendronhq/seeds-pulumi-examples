---
id: testing-unit-go
title: Testing Unit Go
desc: ''
updated: 1617203999590
created: 1617203999590
isDir: false
gitNotePath: '{{ noteHiearchy }}/README.md'
sources:
  - name: pulumi examples
    url: 'https://github.com/pulumi/examples'
    license: Apache License 2.0
---
# Unit Testing Pulumi programs in Go

An example of writing mock-based unit tests with both infrastructure definition and tests written in Go.

## Prerequisites

[Install Go](https://golang.org/doc/install).

## Running the tests

2. Run the tests:

   ```
   $ go test

   PASS
   ok  	testing-unit-go	0.400s
   ```

## Further steps

Learn more about testing Pulumi programs:

- [Testing Guide](https://www.pulumi.com/docs/guides/testing/)
- [Unit Testing Guide](https://www.pulumi.com/docs/guides/testing/unit/)

* * *

## Imported Assets

- [Pulumi.yaml](/assets/pulumi.yaml)
- [go.mod](/assets/go.mod)
- [go.sum](/assets/go.sum)
- [main.go](/assets/main.go)
- [main_test.go](/assets/main_test.go)

