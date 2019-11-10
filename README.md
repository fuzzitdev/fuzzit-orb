# Fuzzit Orb for CircleCI

## What is Fuzzit Orb

This orb helps integrate continuous fuzzing via Fuzzit.dev to your CircleCI workflow.

This orb provides 3 main features: downloading latest version fo fuzzit cli, running fuzzing
on fuzzit.dev and running local fuzzing regression.

## Usage

#### Download only

```yaml
version: 2.1
orbs:
  fuzzit: fuzzitdev/fuzzit@x.y.z
jobs: 
  build:
    docker:
      - image: circleci/golang:1.12
    working_directory: /go/src/github.com/fuzzitdev/example-go

    steps:
      - checkout
      - fuzzit/download
      - run: ./fuzzit.sh fuzzing
```

#### Download + fuzzing/local-regression
```yaml
version: 2.1
orbs:
  fuzzit: fuzzitdev/fuzzit@x.y.z
jobs: 
  build:
    docker:
      - image: circleci/golang:1.12
    working_directory: /go/src/github.com/fuzzitdev/example-go

    steps:
      - checkout
      - fuzzit/fuzzing # or local-regression, this will call the fuzzit.sh script
```

#### Additional parameters

`FUZZIT_API_KEY` should be passed. More info about the fuzzit CLI can be found at
[https://github.com/fuzzitdev/fuzzit](https://github.com/fuzzitdev/fuzzit)
