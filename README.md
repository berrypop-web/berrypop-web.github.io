---

editor: 
  markdown: 
    wrap: 72
---

# berrypop-web.github.io

My personal website and blog, built with Quarto. It includes one personal blog post documenting my first week in MDS, and two computational posts analyzing breast cancer data: one in Python and one in R.

## Requirements

Install these first:

- [Quarto](https://quarto.org/docs/get-started/) <version>
- [uv](https://docs.astral.sh/uv/getting-started/installation/) <version>
- [R](https://cran.r-project.org/) <version>

uv installs the pinned Python version (<version>) automatically, and renv installs itself the first time R starts in this project.

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

## View the site

The built site is written to `docs/`. Open it locally with:

``` bash
open docs/index.html
```

The live site is at https://berrypop-web.github.io.

## Data

Both datasets ship inside packages, so no data files are stored in this repository and rendering does not fetch data from the internet. An internet connection is only needed in steps 2 and 3 to install packages.

- Python post: Breast Cancer Wisconsin (Diagnostic), UCI Machine Learning Repository (CC BY 4.0), via scikit-learn's `load_breast_cancer()`.
- R post: Breast Cancer Wisconsin (Original), UCI Machine Learning Repository (CC BY 4.0), via the `mlbench` package.
