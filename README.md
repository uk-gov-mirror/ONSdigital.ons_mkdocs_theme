<p align="center" style="padding: 50px">
    <img src="ons_mkdocs_theme/assets/images/logo.svg" width="450px">
</p>

## :art: Design standards

Our design standards are available on the FSA Brand Hub:
https://brandhub.food.gov.uk/d/EFmxfa6xzAAW

## :red_car: Getting Started

Setting up your documentation site to use this theme is straightforward. We recommend using modern Python dependency managers like [Poetry][poetry] or [UV][uv] for the best experience.

To be able to use this theme, you need to be using at least **Python v3.10**.

### :computer: Installation

#### with Poetry

Add FSA MkDocs Theme to your project's dependencies:

```
poetry add fsa_mkdocs_theme
```

#### with UV

Install the theme using UV:

```
uv pip install fsa_mkdocs_theme
```

Both will automatically install compatible versions of all dependencies:
[MkDocs], [Markdown], [Pygments] and [Python Markdown Extensions][Python Markdown Extensions].

#### with git

FSA MkDocs Theme can be directly used from [GitHub] by cloning the
repository into a subfolder of your project root folder.

Simply create a folder called `fsa_mkdocs_theme`. In the terminal, ensure you are in the root folder directory of your project and run the following command:

```
mkdir fsa_mkdocs_theme
```

You then need to `cd` into the new directory with the following command:

```
cd fsa_mkdocs_theme
```

To clone the theme files, run the following command:

```
git clone https://github.com/FoodStandardsAgency/fsa_mkdocs_theme
```

Next, install the theme and its dependencies with Poetry or UV:

```
poetry install
```

or

```
uv sync
```

[GitHub]: https://github.com/FoodStandardsAgency/fsa_mkdocs_theme
[poetry]: https://python-poetry.org/
[uv]: https://docs.astral.sh/uv/
[semantic versioning]: https://semver.org/
[MkDocs]: https://mkdocs.org
[Markdown]: https://python-markdown.github.io/
[Pygments]: https://pygments.org/
[Python Markdown Extensions]: https://facelessuser.github.io/pymdown-extensions/
