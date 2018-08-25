# Downson

> markDOWN Object Notation

Downson makes it possible to embed typed and structured data into Markdown documents.

**Specification**

Read the specification here: [SPECIFICATION.md](SPECIFICATION.md).

## Examples

  * The classic "Hello, World!" example:
    * downson
      ~~~~Markdown
      My favorite **.greeting** [](right) is "[Hello, world!](string)".
      ~~~~
    * JSON
      ~~~~JSON
      {
        "greeting": "Hello, World!"
      }
      ~~~~
  * Configuring available and default languages:
    * downson
      ~~~~Markdown
      The available **.languages** [](right) are the following:

        1. [Hungarian](string "hun"),
        1. [English](string "eng"),
        1. [German](string "ger").

      The **.default language** [](right "default") is set to [Hungarian](string "hun").
      ~~~~
    * JSON
      ~~~~JSON
      {
        "languages": [
          "hun",
          "eng",
          "ger"
        ],
        "default": "hun"
      }
      ~~~~
  * Describing your PC to your friend:
    * downson
      ~~~~Markdown
        - Let me show you this **.bad boy** [](right:object "configuration")! It has [8](int) **.cores** [](left) and [16](int) gigs of **.memory** [](left)! []($) **.Impressive** [](right "isImpressive"), huh?
        - [Of course](boolean, "true"), bro!
      ~~~~
    * JSON
      ~~~~JSON
      {
        "configuration": {
          "cores": 8,
          "memory": 16
        },
        "isImpressive": true
      }
      ~~~~
  * Type parameters and custom types:
    * downson
      ~~~~Markdown
      My **.favorite color** [](right "favorite") is [aquamarine](rgb:mode=string), but I also **.like** [](right) [#FFFFFF](rgb:mode=hex).
      ~~~~
    * JSON
      ~~~~JSON
      {
        "favorite": {
          "r": 127,
          "g": 255,
          "b": 212
        },
        "like": {
          "r": 255,
          "g": 255,
          "b": 255
        }
      }
      ~~~~

Larger examples can be found in the [examples](examples) directory.

## Motivation

Downson was created out of pure frustration. Applications ship with tons of configuration and data files that contain crucial settings and information. Yet, correctly documenting these is a horrible burden. One can write the documentation in a separate file, exposing themselves to an increased risk of diverging settings and documentation, or write some sort of rudimentary documentation using in-place comments (assuming, the spec has them).

Current formats embed documentation into the data.

Downson inverts this principle. Data is embedded right into the documentation, offering a structured and sane approach for both the data and its documentation.

Summing this up:

<div align="center">

![Roll safe your configuration!](img/roll-safe.jpg)

</div>

## Goals and non-goals

  * Downson aims to be easily read by **humans** and easily written by **humans**.
  * Downson is **NOT** a data exchange format. It is best suited for configuration and other read-only data files.

## Test Suite

This repository contains a test suite that can be used to exercise downson implementations. The description of the test cases can be found in the [TESTS.md](TESTS.md) downson file.

## Implementations

| Project                                                      | Description                               | Language   |
|--------------------------------------------------------------|-------------------------------------------|:----------:|
| [downson-js](https://github.com/battila7/downson-js)         | A downson parser library based on marked. | JavaScript |
| [downson-js-cli](https://github.com/battila7/downson-js-cli) | A command-line downson-to-JSON converter. | JavaScript |

## License

The contents of this repository are licensed under the MIT License – see [LICENSE](LICENSE).
