# Entropy-to-Zentrube: Redefining Entropy — White Papers (v1.8)

![GitHub Release](https://img.shields.io/github/v/release/OMPSHUNYAYA/Entropy-to-Zentrube?style=flat&logo=github) 
![GitHub Stars](https://img.shields.io/github/stars/OMPSHUNYAYA/Entropy-to-Zentrube?style=flat&logo=github)
![License](https://img.shields.io/badge/license-CC%20BY--NC%204.0-blue?style=flat&logo=creative-commons)

This repository hosts the public release of **Zentrube**, a compact, time-aware entropy lens for symbolic drift.  
It reframes entropy as readiness: rising with rupture, falling with recovery, and remaining bounded and interpretable.


## White Papers
- [Brief Version (v1.8) — Preview on GitHub](Brief_Zentrube_White%20Paper_v1.8.pdf)  
  [📄 Download Brief Version](https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/raw/main/Brief_Zentrube_White%20Paper_v1.8.pdf)  

- [Detailed Version (v1.8) — Preview on GitHub](Zentrube_White%20Paper_v1.8.pdf)  
  [📄 Download Detailed Version](https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/raw/main/Zentrube_White%20Paper_v1.8.pdf)  

## Canonical Formula
Zentrubeₜ = log(Var(x₀:ₜ) + 1) × exp(−λt)  

- **Logarithmic compression** stabilizes heavy tails.  
- **Exponential decay** introduces a tunable memory horizon (≈ 1/λ).  
- As Var → 0 or λ → ∞, Zentrubeₜ → 0.

## Scope
- **Observation-only demonstrations** (not predictive, not operational).  
- Reproducible with public datasets across climate, physiology, telecom, finance, cybersecurity, and more.  
- Designed to complement classical entropy by providing a bounded, interpretable view of drift.

## Hero Use Cases
- 🌪 **Hurricanes (climate):** 20–30% earlier drift signals vs category thresholds.  
- ❤️ **ECG (physiology):** 15–25% earlier anomaly visibility with fewer false positives.  
- 🔐 **Cybersecurity:** earlier DoS onset detection with clear rupture/recovery polarity.  
- 📈 **Insurance:** moderates tail risks by ~20–30% through entropy-tempered valuation.  
- 📡 **Telecom:** 150–200 ms earlier jitter anticipation in join traces.  
- ❄ **Snowfall (meteorology):** drift flagged 7–14 days before major accumulations.  

(All results are **observation-only, reproducible, falsifiable**, and included in the white papers.)

## Quick Start (Python)

A robust quick-start script with variance, Shannon entropy, and Zentrube:

    from collections import Counter
    import math
    import numpy as np

    def zentrube(x, lam=0.02, S="var"):
        """
        Zentrubeₜ = log(S(x₀:ₜ) + 1) × exp(−λt)
        - lam: decay rate (1/lam ≈ memory horizon)
        - S: "var" (variance) or "std" (standard deviation)
        Notes:
        - Uses population variance/std by default (ddof=0).
          If you require sample statistics, adjust with ddof=1 as needed.
        """
        arr = np.asarray(x, dtype=float).reshape(-1)
        t = arr.size
        if t == 0:
            return 0.0
        spread = np.var(arr) if S == "var" else np.std(arr)
        return math.log(spread + 1.0) * math.exp(-lam * t)

    def shannon_entropy(x, base="e"):
        """
        Shannon entropy H(X) = −Σ p(x) log(p(x))
        base: "e" (nats), "2" (bits), or "10" (bans).
        Note:
        - Treats input values as discrete symbols for this demo.
          For continuous data, discretization/binning is typically used.
        """
        arr = np.asarray(x)
        n = arr.size
        if n == 0:
            return 0.0
        counts = Counter(arr)
        probs = [c/n for c in counts.values()]
        if base == "e":
            log = math.log
        elif base == "2":
            log = lambda v: math.log(v, 2)
        else:
            log = lambda v: math.log(v, 10)
        return -sum(p * log(p) for p in probs if p > 0.0)

    # Example dataset
    x = [1, 2, 3, 4, 5, 6]

    print("Variance:", np.var(x))  # ≈ 2.9167 (population)
    print("Shannon Entropy (nats):", shannon_entropy(x))  # ≈ 1.7918
    print("Zentrube (lam=0.02):", zentrube(x, lam=0.02))  # ≈ 1.2109

Typical output (rounded):  
- Variance ≈ **2.92** (unbounded, scale-dependent).  
- Shannon Entropy ≈ **1.79** (nats; distribution-centric, no time).  
- Zentrube ≈ **1.21** (bounded, interpretable, time-aware readiness).

*Tip: λ controls the memory horizon. A typical range is 0.01–0.05; 1/λ ≈ number of steps remembered.*

## How to read the value (plain English)
- If **Zentrube rises**, the system is **rupturing** (variance growing, instability forming).  
- If **Zentrube falls**, the system is **recovering** (variance stabilizing, order returning).  
- Because of the **exp(−λt)** term, older data counts less — the value is always **bounded and time-aware**.

## Quick Comparison

| Measure          | Formula                               | Example (x = [1..6]) | Key Traits                          |
|------------------|----------------------------------------|----------------------|-------------------------------------|
| Variance         | Var(x₀:ₜ)                              | ≈ **2.92**           | Unbounded, scale-dependent          |
| Shannon Entropy  | −Σ p(x) log(p(x))                      | ≈ **1.79** (nats)    | Distribution-centric, no time       |
| Zentrube         | log(Var(x₀:ₜ) + 1) × exp(−λt)          | ≈ **1.21**           | Bounded, time-aware readiness       |

➡️ **Impact:** Zentrube gives a compact, early-warning style number that’s easy to compare across windows, signals, and domains.

## License
© The Authors of **Shunyaya Framework** and **Zentrube Formula**.  
Released under **CC BY-NC 4.0** (non-commercial, with attribution).  
Use for research, review, and education. Commercial use and resale prohibited.

## Latest Release
👉 [Entropy-to-Zentrube: Redefining Entropy — White Papers v1.8](https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/releases/tag/v1.8)

---

## Suggested GitHub Topics (add in repo settings → “About”)
`entropy` · `information-theory` · `drift-detection` · `time-series` · `resilience` · `zentrube` · `shunyaya`
