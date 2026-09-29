# berrypop-web.github.io

My personal website and blog, built with Quarto. It includes one personal blog post documenting my first week in MDS, and two computational posts analyzing breast cancer data (one in Python and one in R), and a bonus post that passes data between R and Python in one document.

## Requirements

Install these first:

- [Quarto](https://quarto.org/docs/get-started/) 1.10.18
- [uv](https://docs.astral.sh/uv/getting-started/installation/) 0.12.7
- [R](https://cran.r-project.org/) 4.6.1

uv installs the pinned Python version 3.14 automatically, and renv installs itself the first time R starts in this project.

## Build the site

1.  Clone the repository and move into it (terminal):

``` bash
   git clone https://github.com/berrypop-web/berrypop-web.github.io.git
   cd berrypop-web.github.io
```

2.  Install the Python environment from `uv.lock` (terminal):

``` bash
   uv sync
```

3.  Install the R packages from `renv.lock` (terminal, from the top level):

``` bash
   R -e "renv::restore()"
```

If asked whether to proceed, type `y`.

4.  Render the site (terminal, from the top level):

``` bash
   uv run quarto render
```

Note: The bonus post runs Python from R using reticulate. `.Rprofile` points reticulate at the project's `.venv`, so step 2 must be done before rendering.

Always render with `uv run` so Quarto uses the project's Python environment. If Python chunks use the wrong environment, delete the Quarto cache and render again:

``` bash
   rm -r .quarto
   uv run quarto render
```

## View the site

The built site is written to `docs/`. Open `docs/index.html` in any web browser. On macOS, you can also run:

``` bash
open docs/index.html
```

The live site is at https://berrypop-web.github.io.

## Data

Both datasets ship inside packages, so no data files are stored in this repository and rendering does not fetch data from the internet. An internet connection is only needed in steps 2 and 3 to install packages.

- Python post: Breast Cancer Wisconsin (Diagnostic), UCI Machine Learning Repository (CC BY 4.0), via scikit-learn's `load_breast_cancer()`.
- R post: Breast Cancer Wisconsin (Original), UCI Machine Learning Repository (CC BY 4.0), via the `mlbench` package.
