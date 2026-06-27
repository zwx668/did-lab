# DiD Lab &mdash; Difference-in-Differences Online Analysis

An interactive web tool for performing **classic Difference-in-Differences (DID)** analysis directly in the browser. Designed for students and researchers who want a quick, intuitive way to estimate treatment effects and visualize parallel trends.

## Live Demo

**[Launch the App](https://zwx668.github.io/did-lab/standalone.html)**

## What It Does

- **Classic 2x2 DID**: One treatment group, one control group, two periods (pre and post)
- **Multi-Period Single-Cohort DID**: Panel data with multiple time periods; all treated units receive treatment at the same time
- **Two-Way Fixed Effects (TWFE)**: Controls for both unit and time fixed effects
- **Parallel Trends Testing**: Event study chart showing treatment effects by relative period
- **Clustered Standard Errors**: Cluster-robust inference at the unit level
- **Instant Results**: Optimized within-transformation estimator &mdash; works with datasets of any size

## What It Does Not Support (Yet)

- Staggered DID (units treated at different times) &mdash; use R's `did` package or Stata's `csdid` instead
- Continuous treatment intensity
- Triple differences (DDD)
- Synthetic control method (SCM)

## How to Use

1. **Upload your data** (.csv, .xlsx, or .xls). Your file must contain at minimum:
   - `id` &mdash; unit identifier
   - `year` &mdash; time variable
   - `treated` &mdash; 1 = treatment group, 0 = control (constant over time)
   - `post` &mdash; 1 = after policy, 0 = before (0 for all control units)
   - `y` &mdash; outcome variable
2. **Map your variables** using the dropdown menus
3. **Run the analysis** &mdash; results appear instantly with regression table and event study chart

### Example Datasets

Two built-in examples are available on the upload page:

| Dataset | Source | Design |
|---------|--------|--------|
| Card & Krueger (1994) | AER, NJ-PA minimum wage | Classic 2x2 |
| Teaching Demo | Simulated | Multi-period single-cohort |

## Local Development

```bash
python -m http.server 8080
# Then open http://localhost:8080/standalone.html
```

## Technology

- Zero dependencies for computation &mdash; matrix operations, OLS, and cluster-robust SE are all implemented in vanilla JavaScript
- SVG-based charts &mdash; no charting library needed
- SheetJS (xlsx.min.js) for Excel file parsing

## Acknowledgments

John Snow (1855) first applied difference-in-differences logic to trace the cholera source. Orley Ashenfelter (1978) introduced DID to modern econometrics. David Card and Alan B. Krueger (1994) advanced the causal inference revolution through their minimum wage research.

## Author

Zhou Wenxuan &mdash; zwx2907899859@163.com

## License

MIT
