<div align="center">

<img src="https://raw.githubusercontent.com/akamhy/waybackpy/master/assets/waybackpy_logo.svg"><br>

<h3>Python package & CLI tool that interfaces with the Wayback Machine API</h3>

</div>

<p align="center">
<a href="https://pypi.org/project/waybackpy/"><img alt="pypi" src="https://img.shields.io/pypi/v/waybackpy.svg"></a>
<a href="https://github.com/akamhy/waybackpy/blob/master/CONTRIBUTING.md"><img alt="Contributions Welcome" src="https://img.shields.io/static/v1.svg?label=Contributions&message=Welcome&color=0059b3&style=flat-square"></a>
<a href="https://pepy.tech/project/waybackpy?versions=2*&versions=1*&versions=3*"><img alt="Downloads" src="https://pepy.tech/badge/waybackpy/month"></a>
<a href="https://github.com/akamhy/waybackpy/commits/master"><img alt="GitHub lastest commit" src="https://img.shields.io/github/last-commit/akamhy/waybackpy?color=blue&style=flat-square"></a>
<a href="#"><img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/waybackpy?style=flat-square"></a>
</p>

-----------------------------------------------------------------------------------------------------------------------------------------------

## ⭐️ Introduction
Waybackpy is a [Python package](https://www.udacity.com/blog/2021/01/what-is-a-python-package.html) and a CLI tool that interfaces with the Wayback Machine API.

 Wayback Machine has 3 client side APIs.

  - Save API
  - Availability API
  - CDX API

All three of these can be accessed by waybackpy.


### 🏗 Installation

Using [pip](https://en.wikipedia.org/wiki/Pip_(package_manager)):

```bash
pip install waybackpy
```

Install directly from GitHub:

```bash
pip install git+https://github.com/akamhy/waybackpy.git
```

### Docker Image
Docker Hub : <https://hub.docker.com/r/secsi/waybackpy>

Docker image is automatically updated on every release by [Regulary and Automatically Updated Docker Images](https://github.com/cybersecsi/RAUDI) (RAUDI). 

RAUDI is a tool by SecSI (<https://secsi.io>), an Italian cybersecurity startup.



### Usage

#### As a Python package
```python
>>> import waybackpy

>>> url = "https://en.wikipedia.org/wiki/Multivariable_calculus"
>>> user_agent = "Mozilla/5.0 (Windows NT 5.1; rv:40.0) Gecko/20100101 Firefox/40.0"

>>> wayback = waybackpy.Url(url, user_agent)

>>> archive = wayback.save()
>>> archive.archive_url
'https://web.archive.org/web/20210104173410/https://en.wikipedia.org/wiki/Multivariable_calculus'

>>> archive.timestamp
datetime.datetime(2021, 1, 4, 17, 35, 12, 691741)

>>> oldest_archive = wayback.oldest()
>>> oldest_archive.archive_url
'https://web.archive.org/web/20050422130129/http://en.wikipedia.org:80/wiki/Multivariable_calculus'

>>> archive_close_to_2010_feb = wayback.near(year=2010, month=2)
>>> archive_close_to_2010_feb.archive_url
'https://web.archive.org/web/20100215001541/http://en.wikipedia.org:80/wiki/Multivariable_calculus'

>>> wayback.newest().archive_url
'https://web.archive.org/web/20210104173410/https://en.wikipedia.org/wiki/Multivariable_calculus'
```
> Documentation at <https://github.com/akamhy/waybackpy/wiki/Python-package-docs>.


#### As a CLI tool
```bash
$ waybackpy --save --url "https://en.wikipedia.org/wiki/Social_media" --user_agent "my-unique-user-agent"
https://web.archive.org/web/20200719062108/https://en.wikipedia.org/wiki/Social_media

$ waybackpy --oldest --url "https://en.wikipedia.org/wiki/Humanoid" --user_agent "my-unique-user-agent"
https://web.archive.org/web/20040415020811/http://en.wikipedia.org:80/wiki/Humanoid

$ waybackpy --newest --url "https://en.wikipedia.org/wiki/Remote_sensing" --user_agent "my-unique-user-agent"
https://web.archive.org/web/20201221130522/https://en.wikipedia.org/wiki/Remote_sensing
```
> CLI documentation is at <https://github.com/akamhy/waybackpy/wiki/CLI-docs>.

### 🛡 License
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/akamhy/waybackpy/blob/master/LICENSE)

Released under the MIT License. See [license](https://github.com/akamhy/waybackpy/blob/master/LICENSE) for details.
