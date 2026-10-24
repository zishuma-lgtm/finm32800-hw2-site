# HW 2: The Yield Curve and the Policy Path

Last updated: {sub-ref}`today`



## Table of Contents

```{toctree}
:maxdepth: 1
:caption: Notebooks 📖
CRSP Treasury Data Overview <cb/notebooks/hw2/01_CRSP_treasury_overview_ipynb>
Replicating GSW (2006) Yield Curve <cb/notebooks/hw2/02_replicate_GSW2005_ipynb>
30-Day Fed Funds Futures Data <cb/notebooks/hw2/01_fed_funds_futures_data_ipynb>
Replicating the CME FedWatch Tool <cb/notebooks/hw2/02_fedwatch_replication_ipynb>
```



```{toctree}
:maxdepth: 1
:caption: Pipeline Charts 📈
cb/charts.md
```

```{postlist}
:format: "{title}"
```


```{toctree}
:maxdepth: 1
:caption: Pipeline Dataframes 📊
cb/dataframes/hw2/crsp_treasury_consolidated.md
cb/dataframes/hw2/fed_funds_futures.md
cb/dataframes/hw2/fed_yield_curve.md
```


```{toctree}
:maxdepth: 1
:caption: Appendix 💡
myst_markdown_demos.md
apidocs/index
```


## Pipeline Specs
| Pipeline Name                   | HW 2: The Yield Curve and the Policy Path                       |
|---------------------------------|--------------------------------------------------------|
| Pipeline ID                     | [hw2](./index.md)              |
| Maintainer                      | Jeremiah Bejarano               |
| Contributors                    | Jeremiah Bejarano |
| Repository                     | https://github.com/hw-finm-32800/hw2                  |
| Pipeline Web Page               | <a href="file:///Users/wanwan/Desktop/hw2-zishuma-lgtm-main/docs/index.html">Pipeline Web Page      |
| Date of Last Code Update        | 2026-10-24 14:44:52           |
| OS Compatibility                | Windows, Linux, macOS |
| Linked Dataframes               |  [hw2:crsp_treasury_consolidated](cb/dataframes/hw2/crsp_treasury_consolidated.md)<br>  [hw2:fed_yield_curve](cb/dataframes/hw2/fed_yield_curve.md)<br>  [hw2:fed_funds_futures](cb/dataframes/hw2/fed_funds_futures.md)<br>  |


**Build Commands:**
```
doit

```


**Due: Tuesday, October 27, at the start of class.** Also posted on Canvas.

This README is the primary source of truth for the assignment. The
[course textbook](https://finm-32800.github.io/HW2.html) has the supporting
notes and the HW guides.

Two replications and three reports. The first replication estimates the U.S.
Treasury yield curve from CRSP quotes, following Gürkaynak, Sack, and Wright
(2006), and checks it against the curve the Federal Reserve publishes every
day. The second reads the expected path of the policy rate out of 30-Day Fed
Funds futures, the way the CME FedWatch tool does. The pipeline then reports
what it found three ways: as notebooks that `doit` executes, as a website
built by ChartBook, and as a two-page PDF market brief compiled from LaTeX.

## How to work on this

Everything here runs as a pipeline. The way to work is:

1. **Run `doit` first.** It pulls the CRSP Treasury files from WRDS, which
   takes a few minutes and about 300 MB, and then stops at the first step that
   depends on a blank. That is expected.
2. **Then run `pytest`.** Read the first failing test, write the code that
   makes it pass, and run it again.
3. **Run `doit` again.** Each blank you fill lets the pipeline get one step
   further. You are done when `doit` finishes without an error and a second
   `doit` reports that every task is up to date.

The unit tests are the specification. When you are unsure what a function or
a task is supposed to produce, read its test in `src/test_*.py`.

**Search for `TODO` to find every blank you need to fill.** They are in
`src/gsw2006_yield_curve.py`, `src/pull_fed_funds_futures.py`,
`src/fedwatch.py`, `src/create_market_brief.py`, `reports/market_brief.tex`,
`dodo.py`, and `chartbook.toml`. Two more files hold what you report
yourself: `src/github_skills.py` and `src/published_site.py`.

Compared with HW 1, less of this assignment is the method and more of it is
the pipeline around the method: one parameter block of a data pull, two
formulas for each replication, and then the reporting end, which is where
most of the blanks are.

**Do not edit the test files.** If a `test_*.py` file is modified, you will be
asked to rewrite your commit history to remove any trace of the edit.

The assignment has four parts, and each test is worth one point.

## Part A: GitHub Skills (3 points)

Complete these three tutorials from the [GitHub Skills](https://skills.github.com/)
page, using **public repositories** in your own GitHub account:

- [GitHub Pages](https://github.com/skills/github-pages)
- [Review pull requests](https://github.com/skills/review-pull-requests)
- [Resolve merge conflicts](https://github.com/skills/resolve-merge-conflicts)

Then open [`src/github_skills.py`](src/github_skills.py), set each
`I_HAVE_COMPLETED_...` flag to `True`, and paste the URL of your completed
public repository. Do the GitHub Pages tutorial before the last step of
Part D, which uses it.

## Part B: the Treasury yield curve (4 points)

The Federal Reserve publishes a Treasury yield curve every day. It is a
Nelson-Siegel-Svensson curve fit to the prices of Treasury notes and bonds,
with the method of
[Gürkaynak, Sack, and Wright (2006)](https://www.federalreserve.gov/pubs/feds/2006/200628/200628abs.html).
Fit the same curve to CRSP Treasury quotes and compare yours with theirs.

Guides:
[CRSP Treasury Data Overview](https://finm-32800.github.io/notebooks/_01_CRSP_treasury_overview_ipynb.html)
and
[Replicating the Gürkaynak, Sack, and Wright (2006) Treasury Yield Curve](https://finm-32800.github.io/notebooks/_02_replicate_GSW2005_ipynb.html)

- **The curve** (`src/gsw2006_yield_curve.py`): complete `spot`, the
  Nelson-Siegel-Svensson formula for the zero-coupon yield at each maturity,
  and `discount`, the discount factor it implies. Each docstring states the
  formula and the second guide explains it. The rest of the file, including
  the fit and the security filter, is complete and calls these two.

`doit` then downloads the Fed's published curve and runs
`src/calc_gsw_fits.py`, which fits the curve on three validation dates and on
the most recent date and saves the tables that the guide and the market brief
load. Both tasks are written for you. Read them in `dodo.py`: you will write
two like them in Part D.

**Does the replication match?** Two of the tests fit your curve to the CRSP
quotes on four dates and check it against the Fed. One compares the prices
your fit implies, bond by bond, with actual prices and with the prices the
Fed's parameters imply. The other, `test_gsw_fits_match_fed`, compares your
fitted yields with the yields the Fed publishes at every maturity from 1 to
30 years and requires them to be within 25 basis points. The second guide
shows the comparison as a table and a chart.

## Part C: the policy path (5 points)

A 30-Day Fed Funds futures contract settles at 100 minus the average
effective fed funds rate over its month, so its price is the market's forecast
of that average. From the contract for the month of the next FOMC meeting you
can back out the rate the market expects after the meeting, and from that the
probability of a hike or a cut. This is what the
[CME FedWatch tool](https://www.cmegroup.com/markets/interest-rates/cme-fedwatch-tool.html)
reports.

Guides:
[30-Day Fed Funds Futures Data from Databento](https://finm-32800.github.io/notebooks/_01_fed_funds_futures_data_ipynb.html)
and
[Replicating the CME FedWatch Tool](https://finm-32800.github.io/notebooks/_02_fedwatch_replication_ipynb.html)

- **The pull** (`src/pull_fed_funds_futures.py`): set the four parameters of
  the Databento query: the dataset, the schema, the symbol, and the kind of
  symbol it is. The first guide explains each one. The cost check and the
  rest of the pull are written.
- **The math** (`src/fedwatch.py`): the second guide derives it; turn it into
  code in `implied_rate`, `solve_post_meeting_rate`, and `move_probability`.

All of these tests run offline, on hand-computed numbers, so you can work on
this part before the futures data is pulled.

**Does the replication match?** The last test,
`test_fedwatch_matches_cme_snapshot`, runs your three functions on the inputs
for a day on which we recorded what the CME tool displayed
(`data_manual/cme_fedwatch_snapshots.csv`) and requires your probability to
land within two price ticks of CME's. The second guide shows the comparison
and explains why the two are close and not identical.

The pull itself needs a Databento API key in your `.env`. You should already
have one; if you do not, email the program administrator, Eliza Higbee. See
[Databento](https://finm-32800.github.io/Week7/databento.html) in the
textbook, and the
[`databento/` examples](https://github.com/finm-32800/inclass_examples/tree/main/databento)
in the in-class examples repository, which show the same kind of pull in
small steps: the Python client, the raw HTTP API, and how to check what a
query costs before you run it. The data this assignment pulls is free under
the course's subscription, and the pull script checks the cost before it
downloads anything and refuses to proceed unless the cost is $0.00.

## Part D: reports (7 points)

A pipeline's results have to land somewhere people can read them. Each piece
below is a build target: `doit` regenerates it whenever the code or the data
behind it changes.

- **Notebooks as tasks** (`dodo.py`, 1 point): the notebooks here only present
  results, and `doit` executes them. The two yield curve notebooks are already
  listed in `notebook_tasks`. Add the two FedWatch notebooks, each with the
  modules it imports and the data files it loads as its file dependencies.
- **The ChartBook manifest** (`chartbook.toml`, 1 point): ChartBook builds a
  website from the executed notebooks and documents the dataframes the
  pipeline pulls. Register the two FedWatch notebooks and the fed funds
  futures dataframe.
- **The LaTeX market brief** (3 points): `reports/market_brief.tex` is a
  two-page brief on the Treasury market. Nothing in it is typed in by hand
  that could be computed: its charts and tables are written by
  `src/create_market_brief.py` and pulled into the document with
  `\includegraphics` and `\input`, so the PDF rebuilds itself from the data.
  Three things to complete:
  - `write_cross_section_stats` in `src/create_market_brief.py`, the function
    that writes the summary statistics as a LaTeX table.
  - The line in `reports/market_brief.tex` that pulls that table in.
  - `task_compile_market_brief` in `dodo.py`, so that `doit` compiles the PDF
    again whenever the document or anything it pulls in changes.

  Compiling needs a LaTeX installation with `latexmk`, such as
  [TeX Live](https://tug.org/texlive/). The tests read your code and your
  `.tex` file, so your points do not depend on your LaTeX installation, but
  compile the brief and read it: `reports/market_brief.pdf`. If LaTeX is new
  to you, work through the [`latex/` examples](https://github.com/finm-32800/inclass_examples/tree/main/latex)
  in the in-class examples repository first. `04_figures_and_tables` covers
  tables, and `08_handout` is a brief built the same way as this one.
- **The published site** (`src/published_site.py`, 2 points): publish the
  ChartBook site with GitHub Pages. The steps are below.

### Publishing the site

Publish from a **separate public repository**. Do not make this assignment
repository public, and do not turn on GitHub Pages in it: it holds your graded
work. The `docs/` folder is gitignored here on purpose.

1. Run `doit`. The `generate_pipeline_site` task writes the site to `docs/`.
   Look at it locally with `chartbook browse`.
2. Create a new **public** repository in your own GitHub account, for example
   `finm32800-hw2-site`. It holds only the built site, never your code, your
   tests, or your `.env`.
3. Copy the built site into it and push. The trailing `/.` copies hidden files
   such as `.nojekyll`:

   ```bash
   git clone https://github.com/<your-username>/finm32800-hw2-site.git
   cp -R docs/. finm32800-hw2-site/
   cd finm32800-hw2-site
   git add .
   git commit -m "Publish ChartBook site"
   git push
   ```

4. In the new repository, turn on GitHub Pages: Settings → Pages → Deploy
   from a branch → `main` / `/ (root)`.
5. When the site is live at
   `https://<your-username>.github.io/finm32800-hw2-site/`, open
   `src/published_site.py`, set the flag to `True`, and paste the address of
   the site.

To update the site later, run `doit`, copy `docs/` again, and push.

## Setup

Use the `finm` environment from HW 0 and HW 1. From the root of this
repository:

```bash
conda activate finm
pip install -r requirements.txt
```

The pinned versions here match HW 1's, and add the Databento client, Plotly,
and IPython, so the same environment keeps serving every repository this
quarter.

Then copy `.env.example` to `.env` and fill in your WRDS username and your
Databento API key:

```bash
cp .env.example .env
```

`.env` is gitignored. Credentials must never be committed. If one ever lands in
a commit, revoke it and generate a new one.

The WRDS pull uses the `.pgpass` file you created for HW 1.

## Grading

Every push runs the test suite on the course runner and posts a score to the
Actions tab. Open the run's summary to see which tests passed and which points
you earned. The 19 graded tests are worth 1 point each, grouped as above. The
suite has other tests too; they check code you do not edit, and they pass once
Part C is done.

The runner grades against its own copy of the pulled data. It does not need
your credentials and never sees your `.env`.

## Other commands

```bash
pytest                      # run the whole suite
pytest src/test_dodo.py     # run one file
doit list                   # show the pipeline's tasks
doit calc_gsw_fits          # run one task
doit forget pull && doit    # pull the futures data again, for the latest prices
doit forget                 # make doit rerun everything it thinks is up to date
chartbook browse            # open the built site in your browser
ruff format . && ruff check --fix .   # format and lint
```

## Directory structure

- `src/` holds the code, the tests, and the notebook sources. The notebooks are
  written as jupytext `.py` files in percent format; `doit` converts and
  executes them. They only present results: the computation is in the
  `pull_` and `calc_` modules, and `doit` runs those first.
- `reports/` holds the LaTeX source of the market brief. The compiled PDF is
  gitignored: it is a build target.
- `_data/` holds pulled data. It is gitignored: everything in it can be
  recreated by running `doit`.
- `_output/` holds generated charts, tables, and rendered notebooks. Also
  gitignored, also recreatable.
- `data_manual/` holds data that is entered by hand and cannot be pulled
  again, here the calendar of FOMC meetings. That is why it is tracked.
- `docs_src/` holds the hand-written page that goes with the FedWatch chart on
  the site. `docs/`, the built site, is gitignored.
- `src/assets/` holds images the notebooks embed that are not generated from
  code, which is why it is tracked.

The `pull_` versus `load_` naming convention matters: a `pull_` function goes
out to an external source, and a `load_` function reads what a previous pull
cached in `_data`. Only the `pull_` functions need credentials.
