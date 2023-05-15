# setup-go

See [setup-go](https://github.com/actions/setup-go/) and specifically the remark to not allow separate binaries to be build using setup-go (too complex) in https://github.com/actions/setup-go/issues/324, and the fix in https://github.com/actions/setup-go/pull/325.

```yaml
steps:
  - uses: actions/checkout@v3
  - uses: actions/setup-go@v3
  - run: go version
```

```yaml
jobs:
  lint:
  steps:
    - uses: actions/checkout@v3
    - uses: hermanbanken/setup-go@v3
      with:
        key: 'job:lint:go'
    - run: go version

  buildA:
    steps:
      - uses: actions/checkout@v3
      - uses: hermanbanken/setup-go@v3
        with:
          key: 'toolA'
      - run: go build ./cmd/a

buildB:
  steps:
    - uses: actions/checkout@v3
    - uses: hermanbanken/setup-go@v3
      with:
        key: 'toolB'
    - run: go build ./cmd/b
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)

# Contributions
Please make changes to [setup-go](github.com/actions/setup-go) first, and only make contributions to this repo to update setup-go.
