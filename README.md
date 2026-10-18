
  # Supplementary Information for PhD Paper 2

  This repository contains supplementary analyses, diagnostic notebooks, and supporting figures for the second
  paper of my PhD research.

  The materials document additional sensitivity tests, methodological checks, and interpretations of the
  relationships between sea-surface temperature anomalies and ocean heat-budget terms.

  ## Repository contents

  - **`get_check_ssta_integration.ipynb`**
    - Examines the relationship between Niño4 sea-surface temperature anomalies (SSTA) and ocean temperature-
    tendency terms in ACCESS-CM2 and ACCESS-OM2.
    - Compares SSTA with raw monthly temperature-tendency anomalies.
    - Tests finite-window integrations of the temperature tendency using a common evaluation period.
    - Includes a synthetic example containing 12-, 40-, and 55-month periodic signals, random noise, and a small
    mean offset.
    - Compares trailing 3-, 6-, 9-, and 12-month sums with the full cumulative synthetic signal.
    - Tests how removing individual periodic components changes the correlation with a fixed cumulative target.
    - Provides a lag-by-lag covariance decomposition of the 9-month rolling-sum correlation.
    - Includes supporting figures explaining the distinction between a monthly tendency, a rolling sum, and a
    cumulative state.

  ## Important terminology
  For a monthly heat-budget term,

  ```math
  Q_i(t) \quad [\mathrm{W\,m^{-2}}],
  ```

  the 9-month rolling sum used in parts of the analysis is

  ```math
  S_i^{9m}(t)
  =
  \sum_{k=0}^{8} Q_i(t-k).
  ```

  Because this calculation does not explicitly multiply by the duration of each month, it is described as a **9-
  month rolling sum of monthly-mean heat-budget terms**, rather than a strict physical time integration.

  A physical time integral would instead be

  ```math
  E_i^{9m}(t)
  =
  \sum_{k=0}^{8} Q_i(t-k)\,\Delta t_{t-k},
  ```

  where $\Delta t_{t-k}$ is the duration of the corresponding month in seconds. The resulting units are

  ```math
  [\mathrm{W\,m^{-2}}]\,[\mathrm{s}]
  =
  [\mathrm{J\,m^{-2}}].
  ```

  ## Reproducibility

  The synthetic experiments use a fixed random seed so that the results can be reproduced:

  ```python
  np.random.seed(42)
  ```

  The notebooks generate figures in the local `figures/` directory.

  ## Additional material

  Further supplementary notebooks, sensitivity tests, and figure descriptions will be added as the analysis
  develops.


