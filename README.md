# metropolis-highD

Numerical calculations and figures for Metropolis random walks escaping deep cubic basins in higher dimensions.

The notebook studies the potential `V(x) = ||x||_inf` on the integer lattice, with nearest-neighbor proposals, uphill acceptance probability `p`, and absorption at shell `N`. It compares the true-chain mean escape time with the shell-quotient formula in dimensions 1, 2, and 3.

## Contents

- [Numerical calculations notebook](Metropolis_Numerical_Calculations_Figures.ipynb): computes the dataset, exploratory Figures 1–3, final paper Figures 4–5, Table I, numerical checks, and high-precision comparison audits.
- [Paper (PDF)](paper/Metropolis_Walks_in_Higher_Dimensions.pdf): accompanying manuscript.
- [LICENSE](LICENSE): BSD 3-Clause license.

## Run the notebook

Open the notebook in [Google Colab](https://colab.research.google.com/github/ANRGUSC/metropolis-highD/blob/main/Metropolis_Numerical_Calculations_Figures.ipynb) and select **Runtime → Run all**.

Alternatively, install the Python dependencies and launch Jupyter locally:

```sh
python -m pip install jupyter numpy pandas scipy matplotlib mpmath
jupyter notebook Metropolis_Numerical_Calculations_Figures.ipynb
```

Run the cells in order. The configuration cell controls the figure grids and optional audits. Results are written to `metropolis_figures_123/`, with data, figures (PDF, SVG, PNG), tables, and a manifest. The notebook also creates `metropolis_figures_123.zip` and downloads it automatically in Colab.

## Figures used in the paper

The notebook's **Paper Section VI — final Figures 4 and 5** section generates the final manuscript figures:

| Paper figure | Description | Output PDF |
|---|---|---|
| 4 | True escape times versus basin depth and dimensional speedup versus acceptance probability | `fig_vi_dimensional_speedup.pdf` |
| 5 | True and shell-quotient escape times versus basin depth, with signed relative discrepancy | `fig_vi_quotient_comparison.pdf` |

These files, along with SVG and PNG versions, are saved in `metropolis_figures_123/figures/`. The final ZIP includes the paper figures, plot data, and captions.

The paper plots use the existing `data/all_results.csv` dataset and require no additional solves with the default configuration. If you change the grids, the paper cells report missing required points. They also check the numerical values quoted in the final Section VI; the earlier notebook checks refer to the earlier draft and Table I.

## Numerical method

The true-chain calculations use exact sign/permutation-orbit lumping, a regenerative identity, and a float64 sparse LU solve. Residual and alternate-ordering checks reject points that fail the configured tolerances. Separate mpmath audits compare selected results at 60 and 90 digits; they do not supply plotted or tabulated values. The notebook does not use Monte Carlo simulation.

The shell-quotient formula is exact for its quotient chain and agrees with the true walk in one dimension; higher-dimensional comparisons are numerical. Residual and LU-ordering checks are not forward-error certificates. See the notebook and paper for details and limitations.

## License

This repository is distributed under the [BSD 3-Clause license](LICENSE).
