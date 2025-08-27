# Entropy-to-Zentrube: Redefining Entropy — White Papers (v1.8)

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

Try Zentrube in just a few lines of Python:

    import numpy as np

    def zentrube(x, lam=0.01):
        t = len(x)
        return np.log(np.var(x) + 1.0) * np.exp(-lam * t)

    # Example dataset
    x = [1, 2, 3, 4, 5, 6]
    print("Zentrube value:", zentrube(x, lam=0.02))

Output is a single readiness value that reflects both **spread** (via variance) and **recency** (via time decay).

## How to read the value (plain English)
- If **Zentrube rises**, the system is **rupturing** (variance growing, instability forming).  
- If **Zentrube falls**, the system is **recovering** (variance stabilizing, order returning).  
- Because of the **exp(−λt)** term, older data counts less — the value is always **bounded and time-aware**.

## Quick Comparison (Variance vs Shannon vs Zentrube)

To see why Zentrube matters, compare with classical measures:

Formulas:  
- Variance = Var(x₀:ₜ)  
- Shannon Entropy = −Σ p(x) log(p(x))  
- Zentrubeₜ = log(Var(x₀:ₜ) + 1) × exp(−λt)

Example code:

    from collections import Counter
    import math, numpy as np

    def shannon_entropy(x):
        counts = Counter(x)
        total = len(x)
        return -sum((c/total) * math.log(c/total) for c in counts.values())

    def zentrube(x, lam=0.02):
        t = len(x)
        return np.log(np.var(x) + 1.0) * np.exp(-lam * t)

    x = [1, 2, 3, 4, 5, 6]
    print("Variance:", np.var(x))
    print("Shannon Entropy:", shannon_entropy(x))
    print("Zentrube:", zentrube(x))

Typical outcome on this dataset:  
- Variance ≈ 2.92 (unbounded, scale-dependent).  
- Shannon Entropy ≈ 1.79 (distribution-centric, no time element).  
- Zentrube ≈ 1.22 (bounded, interpretable, time-aware drift/readiness).

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

