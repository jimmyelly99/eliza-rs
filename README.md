# eliza-rs
[![Crates.io](https://img.shields.io/crates/v/eliza.svg)](https://crates.io/crates/eliza)
[![Documentation](https://docs.rs/eliza/badge.svg)](https://docs.rs/eliza)
[![Build Status](https://travis-ci.org/arosspope/eliza.svg?branch=master)](https://travis-ci.org/arosspope/eliza)

This rust binary is an implementation of the early natural language processing computer program **ELIZA**. The original program was developed from 1964 to 1966 at the MIT Artificial Intelligence Laboratory by Joseph Weizenbaum.

## Introduction

![convo](http://i.imgur.com/Z69mFI8.gif)

ELIZA simulates conversation by implementing _pattern matching_ and a _substitution methodology_ that gives users an illusion of understanding on the part of the program. Directives on how to process input are provided by 'scripts', (written originally in MAD-Slip, now in json) which allow ELIZA to engage in discourse by following script rules. The most famous script, [DOCTOR](scripts/doctor.json), simulates a Rogerian psychotherapist.

> Weizenbaum, J. (1996), _ELIZA - A computer program for the study of natural language communication between man and machine_, Communications of the ACM, vol 9, issue 1

## Installation

To install this rust binary, one can do so from source or from [crates.io](https://crates.io/crates/eliza). In either case, you need to have the rust compiler and cargo [installed](https://rustup.rs/) on your system.

### From crates.io

Installing `eliza` from crates.io is quite simple with cargo:
```bash
user@foo(~) ~> cargo install eliza
```

### From source

After forking this project and cloning it to your local machine, navigate to the project directory and run:

```bash
user@foo(eliza-rs) ~> cargo build
```

You may also want to optionally run the unit tests to ensure ELIZA is behaving as expected:

```bash
user@foo(eliza-rs) ~> cargo test
```

## Operation

To start an ELIZA session, you must provide the binary with a path to an ELIZA script. This script takes the form of a `json` file. Assuming that you have installed from source and wanted to run the famous DOCTOR program, the command you would run from the project root would be similar to:

```bash
user@foo(eliza-rs) ~> cargo run scripts/doctor.json
```

If instead, you installed from crates.io, then the location of `doctor.json` will be different. Out of convenience I decided to bundle the `doctor.json` script with the eliza binary on crates.io. For each user, it's location will be slightly different, but somewhere in your cargo registry, similar to:

```bash
user@foo(~) ~> eliza .cargo/registry/src/[some_hash]/eliza-[ver]/scripts/doctor.json
```

![running](https://i.imgur.com/RUneq7b.gif)
> _Starting eliza with cargo then leaving the session_

_________

## Writing your own ELIZA script

The beuaty of ELIZA's design methodology means that the role of the programmer and playwright may be seperated. An important property of ELIZA is that a script is data - it is not part of the program itself. Hence, ELIZA is not restricted to a particular set of recognition patterns or responses, indeed not even to any specific language.

As such, contributors may decide to improve the original `doctor.json` script or completely create their own from scratch. A simple example of a [pirate script](scripts/pirate.json) has been included to show how little is needed to start creating something neat.

More information on the structure of a script, can be found in the documentation for the `script` module on [doc.rs](https://docs.rs/eliza).
