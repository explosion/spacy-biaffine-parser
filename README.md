<a href="https://explosion.ai"><img src="https://explosion.ai/assets/img/logo.svg" width="125" height="125" align="right" /></a>

# spacy-biaffine-parser: Biaffine parser for spaCy

[![tests](https://github.com/explosion/spacy-biaffine-parser/actions/workflows/tests.yml/badge.svg)](https://github.com/explosion/spacy-biaffine-parser/actions/workflows/tests.yml)
[![pypi Version](https://img.shields.io/pypi/v/spacy-biaffine-parser.svg?style=flat-square&logo=pypi&logoColor=white)](https://pypi.org/project/spacy-biaffine-parser/)

This package provides a biaffine dependency parser, similar to that proposed in [Deep Biaffine
Attention for Neural Dependency Parsing](Deep Biaffine Attention for Neural
Dependency Parsing) (Dozat & Manning, 2016).

## Installation

Install with `pip`:

```bash
python -m pip install -U pip setuptools wheel
python -m pip install spacy-biaffine-parser
```

## Usage

The parser consists of two pipes:
an edge predicter and an edge labeler. For example:

```ini
[components.arc_predicter]
factory = "arc_predicter"

[components.arc_labeler]
factory = "arc_labeler"
```

The arc predicter requires that a previous component (such as `senter`) sets
sentence boundaries during training. Therefore, such a component must be added
to `annotating_components`:

```ini
[training]
annotating_components = ["senter"]
```

The [biaffine parser sample project](project) provides an example biaffine parser pipeline.

## Bug reports and issues

Please report bugs in the
[spaCy issue tracker](https://github.com/explosion/spaCy/issues) or open a new
thread on the [discussion board](https://github.com/explosion/spaCy/discussions)
for other issues.
