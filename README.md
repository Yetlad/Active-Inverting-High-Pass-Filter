
## Inverting Active High-Pass Filter Design

---

## Objective

The objective of this exercise is to **design and verify an inverting active high-pass filter** with the following specifications:

* **Passband gain** = 2
* **Corner (cutoff) frequency** = 1 krad/s

The circuit is implemented using an operational amplifier and verified using **AC analysis in LTspice**.

---



The transfer function of an inverting first-order active high-pass filter is:

[
H(j\omega) = \frac{-R_f C j\omega}{R_1 C j\omega + 1}
]

From the transfer function:

* **Passband Gain** ((\omega \to \infty)):
  [
  A = -\frac{R_f}{R_1}
  ]

* **Corner Frequency**:
  [
  \omega_c = \frac{1}{R_1 C}
  ]

---

## Task 1 – Filter Design

### Design Requirements

* Passband gain = 2 →
  [
  \frac{R_f}{R_1} = 2
  ]

* Corner frequency = 1 krad/s →
  [
  R_1 C = \frac{1}{1000}
  ]

### Example Component Selection

* ( R_1 = 10,k\Omega )
* ( R_f = 20,k\Omega )
* ( C = 100,nF )

These values satisfy both the gain and corner frequency requirements.

---

## Task 2 – LTspice Circuit

### Circuit Construction

1. Place an **op-amp** (e.g., UniversalOpamp2)
2. Connect:

   * Capacitor ( C ) in series with the input
   * Resistor ( R_1 ) between capacitor and inverting input
   * Feedback resistor ( R_f ) from output to inverting input
   * Non-inverting input to ground
3. Power the op-amp with **±12 V supplies**
4. Set the input source:

   * AC amplitude = **1 V**

---

## Task 3 – AC Analysis

### Simulation Directive

```text
.ac dec 100 1 10k
```

### Output Plot

The frequency response is plotted using:

```text
db(V(out)/V(in))
```

---

## Task 4 – Verification

Using the AC magnitude plot, the following are verified:

1. **Low-Frequency Attenuation**

   * Output magnitude approaches −∞ dB at low frequencies

2. **Passband Gain**

   * Gain ≈ **6 dB**, corresponding to a magnitude of 2

3. **Corner Frequency**

   * −3 dB point occurs at approximately **1 krad/s**

4. The −3 dB point is clearly marked on the plot.

---



## Conclusion

The simulated response closely matches the theoretical design. The inverting active high-pass filter achieves the required passband gain of 2 and a corner frequency of 1 krad/s.

---

