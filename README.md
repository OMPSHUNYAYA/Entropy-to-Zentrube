# Shunyaya Entropy Framework — Zentrube: Time-Aware Entropy That Works
*Entropy-to-Zentrube: Redefining Entropy — White Papers (v1.8)*

![GitHub Release](https://img.shields.io/github/v/release/OMPSHUNYAYA/Entropy-to-Zentrube?style=flat&logo=github)
![GitHub Stars](https://img.shields.io/github/stars/OMPSHUNYAYA/Entropy-to-Zentrube?style=flat&logo=github)
![License](https://img.shields.io/badge/license-CC%20BY--NC%204.0-blue?style=flat&logo=creative-commons)

**Zentrube** is a compact, time-aware entropy signal for symbolic drift—**rises with rupture, falls with recovery, and stays bounded**.

**Six reproducible, observation-grade demonstrations:**
- 🌪 **Hurricanes:** 20–30% earlier drift vs category thresholds  
- ❤️ **ECG:** 15–25% earlier anomaly visibility with fewer false positives  
- 🔐 **Cybersecurity:** earlier DoS onset with clean rupture/recovery polarity  
- 📈 **Insurance:** ~20–30% tail-risk moderation  
- 📡 **Telecom:** 150–200 ms earlier jitter anticipation  
- ❄ **Snowfall:** 7–14 day early drift before major accumulations  

> Prefer to read first? Jump to the white papers below. Want to try code? See **Quick Start**.

---

## Canonical Formula (plain text)

Zentrubeₜ = log(Var(x₀:ₜ) + 1) × exp(−λt)

- Logarithmic compression stabilizes heavy tails  
- Exponential decay introduces a tunable memory horizon (≈ 1/λ)  
- As Var → 0 or λ → ∞, Zentrubeₜ → 0

---

## Why this matters: Classical Entropy vs Zentrube

| Measure           | Formula                               | Key Traits                                |
|-------------------|----------------------------------------|-------------------------------------------|
| Variance          | Var(x₀:ₜ)                              | Unbounded, scale-dependent                |
| Shannon Entropy   | −Σ p(x) log(p(x))                      | Distribution-centric, no time             |
| **Zentrube**      | log(Var(x₀:ₜ) + 1) × exp(−λt)          | **Bounded, time-aware readiness signal**  |

Zentrube compresses volatility and discounts the distant past, giving a clean, comparable “readiness” number that tracks **rupture → recovery**.

---

## Scope

- **Observation-only** demonstrations (not predictive, not operational)  
- Reproducible with public datasets across climate, physiology, telecom, cybersecurity, finance, and more  
- Designed to complement classical entropy with a bounded, interpretable **drift signal**

---

## Quick Start (Python)

A minimal script showing variance, Shannon entropy, and Zentrube:

    from collections import Counter
    import math
    import numpy as np

    def zentrube(x, lam=0.02, S="var", ddof=0):
        """
        Zentrubeₜ = log(S(x₀:ₜ) + 1) × exp(−λt)
        - lam: decay rate (1/lam ≈ memory horizon)
        - S: "var" (variance) or "std" (standard deviation)
        - ddof: 0 for population (default), 1 for sample
        Notes:
        - Uses population statistics by default (ddof=0).
          For sample variance/std, set ddof=1 as needed.
        """
        arr = np.asarray(x, dtype=float).reshape(-1)
        t = arr.size
        if t == 0:
            return 0.0
        if S == "var":
            spread = np.var(arr, ddof=ddof)
        elif S == "std":
            spread = np.std(arr, ddof=ddof)
        else:
            raise ValueError("S must be 'var' or 'std'")
        return math.log(spread + 1.0) * math.exp(-lam * t)

    def shannon_entropy(x, base="e"):
        """
        Shannon entropy H(X) = −Σ p(x) log(p(x))
        base: "e" (nats), "2" (bits), or "10" (bans).
        Treats input as discrete symbols for this quick demo.
        """
        arr = np.asarray(x)
        n = arr.size
        if n == 0:
            return 0.0
        counts = Counter(arr)
        probs = [c/n for c in counts.values()]
        if base == "e":
            logf = math.log
        elif base == "2":
            logf = lambda v: math.log(v, 2)
        elif base == "10":
            logf = lambda v: math.log(v, 10)
        else:
            raise ValueError("base must be 'e', '2', or '10'")
        return -sum(p * logf(p) for p in probs if p > 0.0)

    if __name__ == "__main__":
        # Example dataset
        x = [1, 2, 3, 4, 5, 6]

        # Population variance by default (ddof=0)
        var_pop = np.var(x, ddof=0)              # 2.9166666667
        H_e = shannon_entropy(x, base="e")       # 1.7917594692 (ln(6))
        Z = zentrube(x, lam=0.02, S="var")       # 1.2108601013

        print("Variance (population):", var_pop)
        print("Shannon Entropy (nats):", H_e)
        print("Zentrube (lam=0.02):", Z)

        # Optional self-checks (tolerances)
        assert math.isclose(var_pop, 2.9166666666666665, rel_tol=0, abs_tol=1e-12)
        assert math.isclose(H_e, 1.791759469228055, rel_tol=0, abs_tol=1e-12)
        assert math.isclose(Z, 1.2108601013028597, rel_tol=0, abs_tol=1e-12)

**How to read it (plain English):**
- If **Zentrube rises**, the system is **rupturing** (instability forming)  
- If **Zentrube falls**, the system is **recovering** (stability returning)  
- The **exp(−λt)** term makes it **time-aware** and **bounded**

---

## White Papers

- **Brief Version (v1.8) — Preview on GitHub**  
  [📄 Download Brief Version](https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/raw/main/Brief_Zentrube_White%20Paper_v1.8.pdf)

- **Detailed Version (v1.8) — Preview on GitHub**  
  [📄 Download Detailed Version](https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/raw/main/Zentrube_White%20Paper_v1.8.pdf)

Latest release: **v1.8** → https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/releases/tag/v1.8

---

## Project Links

- Repository: https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube  
- Releases: https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/releases  
- Issues & ideas: https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube/issues

---

## License

© The Authors of **Shunyaya Framework** and **Zentrube Formula**  
Released under **CC BY-NC 4.0** (non-commercial, with attribution).  
Use for research, review, and education. Commercial use and resale prohibited.

---

## How to cite

If you use this work, please cite the repository:

    Shunyaya Framework Authors (2025).
    Entropy-to-Zentrube: Time-aware entropy for drift detection.
    GitHub repository: https://github.com/OMPSHUNYAYA/Entropy-to-Zentrube
    License: CC BY-NC 4.0.

---

## Suggested GitHub Topics (Repo → About)

`entropy` · `information-theory` · `time-series` · `drift-detection` · `anomaly-detection` · `early-warning` · `resilience` · `zentrube` · `shunyaya`
