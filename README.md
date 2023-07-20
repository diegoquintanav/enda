# enda

[![PyPI version](https://badge.fury.io/py/enda.svg)](https://badge.fury.io/py/enda)

## What is it?

**enda** is a Python package that provides tools to manipulate **timeseries** data in conjunction with **contracts** data for analysis and **forecasts**.

Its main goal is to help [Rescoop.eu](https://www.rescoop.eu/) members build various applications, such as short-term electricity load and production forecasts, specifically for the [RescoopVPP](https://www.rescoopvpp.eu/) project. Hence some tools in this package perform TSO (transmission network operator) and DNO (distribution network operator) data wrangling as well as weather data management. enda is mainly developed by [Enercoop](https://www.enercoop.fr/).

## Main Features

Here are some things **enda** does well:

- Provide robust machine learning algorithms for short-term electricty load and production forecasts, developed by Enercoop. The load forecast was originally based on Komi Nagbe's thesis (<http://www.theses.fr/s148364>).
- Manipulate **contracts** data coming from your ERP and turn it into timeseries you can use for analysis, visualisation and machine learning.
- Timeseries-specific detection of missing data, like time gaps and frequency changes.
- Date-time feature engineering robust to timezone hazards.

## Where to get it

The source code is currently hosted on GitHub at: <https://github.com/enercoop/enda>

Binary installers for the latest released version are available at the [Python
Package Index (PyPI)](https://pypi.org/project/enda) (for now it is not directly on [Conda](https://docs.conda.io/en/latest/)).

```sh
# PyPI
pip install enda
```

If you wish to install the dependencies needed to run the examples, you can install `enda` with the `examples` extra:

```sh
pip install enda[examples]
```

You can install all the optional dependencies with the `all` extra:

```sh
pip install enda[all]
```

or using poetry:

```sh
poetry add enda[all]
```

## How to get started?

Check out the guides: <https://github.com/enercoop/enda/tree/main/guides>.

## Hard dependencies

- [Pandas - the main dataframe manipulation tool for python, advanced timeseries management included.](https://pandas.pydata.org/)
- Pandas itself has hard dependencies and optional dependencies, checkout <https://pandas.pydata.org/pandas-docs/stable/getting_started/install.html> . Hard dependencies of pandas include: `setuptools`, `NumPy`, `python-dateutil`, `pytz`.

## Optional dependencies

Optional dependencies are used only for specific methods. Enda will give an error if the method called requires a dependency that is not installed.

Enda can work with different machine learning "backends" :

- [Scikit-learn](https://scikit-learn.org/stable/)
- [H2O - an efficient machine learning framework](https://docs.h2o.ai/)

You can also easily implement your own ml-backend by implementing enda's ModelInterface. Checkout `enda.ml_backends.sklearn_linreg.py` for an example with `SKLearnLinearRegression`.

Other optional dependencies:

- [statsmodel](https://pypi.org/project/statsmodels/)

Furthermore, don't hesitate to install pandas "Recommended dependencies" for speed-ups : `numexpr` and `bottleneck`.

If you want to save your trained models, we recommend `joblib`. See Scikit-learn's recommendations here: <https://scikit-learn.org/stable/modules/model_persistence.html>.

All these dependencies can be installed along `enda` with the following command:

```sh
pip install enda[examples]
```

Or you can install them manually:

```sh
pip install numexpr bottleneck pandas enda jupyter h2o scikit-learn statsmodels joblib matplotlib
```

## About `numpy` support for python 3.7

Support for `numpy` and python 3.7 according to <https://numpy.org/neps/nep-0029-deprecation_policy.html#support-table>
and <https://github.com/scipy/oldest-supported-numpy>

## License

[MIT](LICENSE)

## Contributing

The project can be built using [Poetry](https://python-poetry.org/). You can install it following the instructions here: <https://python-poetry.org/docs/#installation>.

To develop `enda`, you can clone the repository and install the dependencies with poetry:

```sh
git clone https://github.com/enercoop/enda.git
cd enda
poetry install --with dev
```

If you are not using `Poetry` you can install the dependencies with `pip`:

```sh
pip install enda[dev]
```

To run the tests, you can use the following command:

```sh
poetry run pytest # or just pytest if you have activated the virtual environment
```

To run tests using tox, you can use the following command:

```sh
poetry run tox # or just tox if you have activated the virtual environment
```

## Building and publishing

After you have built a new feature, upgraded a dependency or fixed a bug, you need to update the version number in `pyproject.toml` and `enda/__init__.py` and publish the new version to PyPI.

If you are using `Poetry`, you can add the poetry plugin `poetry-bumpversion` to help you with this:

```sh
poetry self add poetry-bumpversion
```

and then you can use the following commands to update the version number:

```sh
poetry version patch # or minor or major
```

See the [`poetry-bumpversion`](https://pypi.org/project/poetry-bumpversion/) documentation for more details:

After that you will need to build the package with:

```sh
poetry build
```

and then you can publish the new version to PyPI:

```sh
poetry publish
```

You will need to setup your PyPI credentials for this to work. See the [Poetry documentation](https://python-poetry.org/docs/repositories/#configuring-credentials) for more details.

