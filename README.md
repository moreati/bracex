[![Donate via PayPal][donate-image]][donate-link]
[![Discord][discord-image]][discord-link]
[![Build][github-ci-image]][github-ci-link]
[![Coverage Status][codecov-image]][codecov-link]
[![PyPI Version][pypi-image]][pypi-link]
[![PyPI - Python Version][python-image]][pypi-link]
![License][license-image-mit]
# Bracex

Bracex is a brace expanding library (à la Bash) for Python. Brace expanding is used to generate arbitrary strings.

```console
$ echo {{a,b},c}d
ad bd cd
```

Bracex adds this ability to Python:

```python
>>> bracex.expand(r'file-{{a,b},c}d.txt')
['file-ad.txt', 'file-bd.txt', 'file-cd.txt']
```

and as a command:

```console
$ python3 -m bracex -0 "base/{a,b}/{1..2}" | xargs -0 mkdir -p
$ tree base/
base/
├── a
│   ├── 1
│   └── 2
└── b
    ├── 1
    └── 2
```

- **Why Bracex over other solutions?**

    Bracex actually follows pretty closely to how Bash processes braces. It is not a 1:1 implementation of how Bash
    handles braces, but generally, it follows very closely. Almost all of the test cases are run through Bash first,
    then our implementation is compared against the results Bash gives. There are a few cases where we have purposely
    deviated. For instance, we are not handling Bash's command line inputs, so we are not giving special meaning to back
    ticks and quotes at this time.

    On the command line Bracex can handle more expansions than Bash itself.

## Install

```console
$ pip install bracex
```

## Documentation

Documentation is found here: https://facelessuser.github.io/bracex/.

## License

MIT License

Copyright (c) 2018 - 2021 Isaac Muse

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[github-ci-image]: https://github.com/facelessuser/bracex/workflows/build/badge.svg?branch=master&event=push
[github-ci-link]: https://github.com/facelessuser/bracex/actions?query=workflow%3Abuild+branch%3Amaster
[discord-image]: https://img.shields.io/discord/678289859768745989?logo=discord&logoColor=aaaaaa&color=mediumpurple&labelColor=333333
[discord-link]:https://discord.gg/TWs8Tgr
[codecov-image]: https://img.shields.io/codecov/c/github/facelessuser/bracex/master.svg?logo=codecov&logoColor=aaaaaa&labelColor=333333
[codecov-link]: https://codecov.io/github/facelessuser/bracex
[pypi-image]: https://img.shields.io/pypi/v/bracex.svg?logo=pypi&logoColor=aaaaaa&labelColor=333333
[pypi-link]: https://pypi.python.org/pypi/bracex
[python-image]: https://img.shields.io/pypi/pyversions/bracex?logo=python&logoColor=aaaaaa&labelColor=333333
[license-image-mit]: https://img.shields.io/badge/license-MIT-blue.svg?labelColor=333333
[donate-image]: https://img.shields.io/badge/Donate-PayPal-3fabd1?logo=paypal
[donate-link]: https://www.paypal.me/facelessuser
