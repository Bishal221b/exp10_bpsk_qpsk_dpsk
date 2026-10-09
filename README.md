# Experiment 10: BPSK, QPSK and DPSK (first-principles simulation)

Coherent BPSK, Gray-coded QPSK and differential BPSK (DPSK) implemented from scratch with
NumPy and Matplotlib. No communications library is used. The mapper, demapper, differential
encoder/detector, AWGN, carrier phase offset and BER counting are all hand-written.

## What it does
- Validates the Gray QPSK mapping for 00, 01, 11, 10 (noiseless and noisy)
- Tests carrier phase offsets of 10, 30, 60 and 90 degrees for BPSK, QPSK and DPSK
- Shows QPSK constellation rotation, phase trajectories and differential phase
- Compares decision statistics (histograms per transmitted class)
- BER vs Eb/N0 against theory, plus BER vs phase offset
- Prints a PASS/FAIL self-check list at the end

## Conventions
- Es = 1 for every scheme. BPSK/DPSK: Eb = 1. QPSK: Eb = Es/2 = 0.5.
- N0 = Eb/(Eb/N0). Noise n = sqrt(N0/2)(N(0,1) + jN(0,1)).
- BPSK: 0 -> -1, 1 -> +1. QPSK: 00 -> +1+j, 01 -> -1+j, 11 -> -1-j, 10 -> +1-j (divided by sqrt 2).
- DPSK: d[0] = +1, d[k] = d[k-1]*b[k]; detect Re(r[k] conj(r[k-1])) >= 0 as bit 1.

## Run
Local:
```
pip install -r requirements.txt
python exp10_bpsk_qpsk_dpsk.py
```
Figures are saved to `exp10_figures/`. Set `SHOW = True` near the top to open windows.
The run takes roughly 15 seconds.

Google Colab: open `exp10_bpsk_qpsk_dpsk.ipynb` (File > Upload notebook, or from GitHub) and choose Runtime > Run all.
If the repository is public, this badge works after you replace USER and REPO:

`[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USER/REPO/blob/main/exp10_bpsk_qpsk_dpsk.ipynb)`

## Files
- `exp10_bpsk_qpsk_dpsk.py`: the full script (`# %%` markers make it runnable cell by cell in VS Code/Spyder)
- `exp10_bpsk_qpsk_dpsk.ipynb`: the same code as a notebook
- `exp10_bpsk_qpsk_dpsk.m`: equivalent MATLAB version (function file, R2015a+)
