[![Build Status](https://travis-ci.org/gmarmstrong/python-datamuse.svg?branch=master)](https://travis-ci.org/gmarmstrong/python-datamuse)

# python-datamuse

Python wrapper and scripts for the [Datamuse API](http://datamuse.com/api/).
Available on PyPI at <https://pypi.python.org/pypi/python-datamuse>. You can
install this library with `pip3 install python-datamuse`.

## Changelog

### Version 1.3.* (2019-09-20)

- Add optional arguments to `suggest` method
- Document and test suggestion method
- **(1.3.1):** Update README example
- **(1.3.1):** Remove WORD_PARAMS
- **(1.3.1):** Document `words` method

### Version 1.2.* (2018-10-23)

- Raise Python version to 3.6
- Mock the Datamuse API for tests
- Restructure project files
- Set README as PyPI long description
- **(1.2.1):** Fix README formatting on PyPI

### Version 1.1.0 (2018-02-18)

- Changed to Python 3
- Uploaded to PyPI, added instructions for PyPI installation
- Changed README example to reflect PyPI packaging
- Set up Travis CI
- Temporarily removed pandas
- Changed mode of scripts to executable

## Example

```python
>>> import datamuse
>>> api = datamuse.Datamuse()
>>> api.words(rel_rhy='ninth', max=5)  # words that rhyme with "ninth"
[]
>>> api.words(rel_rhy='orange', max=5)  # words that rhyme with "orange"
[{'word': 'door hinge', 'score': 74, 'numSyllables': 2}]
>>> api.words(rel_jja='yellow', max=5)  # things often described as "yellow"
[{'word': 'fever', 'score': 1001}, {'word': 'color', 'score': 1000}, {'word': 'flowers', 'score': 999}, {'word': 'light', 'score': 998}, {'word': 'colour', 'score': 997}]
>>> api.suggest(s='foo', max_results=10)  # completion suggestions for "foo"
[{'word': 'food', 'score': 3888}, {'word': 'foot', 'score': 3041}, {'word': 'fool', 'score': 1836}, {'word': 'football', 'score': 1424}, {'word': 'footage', 'score': 1328}, {'word': 'footprint', 'score': 1082}, {'word': 'foolish', 'score': 967}, {'word': 'foof', 'score': 930}, {'word': 'footing', 'score': 786}, {'word': 'foolproof', 'score': 697}]
```

Note that the default number of results is set to 100. You can set the default
`max` to something else using the `set_max_default` method, e.g.
`api.set_max_default(300)`. Datamuse only returns 1000 results max.
