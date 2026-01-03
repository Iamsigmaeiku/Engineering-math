# Engineering Mathematics: Sec 2.7 Review
**Topic:** Nonhomogeneous Linear ODEs (Method of Undetermined Coefficients)  
**Author:** Electrical Engineering Student (NKUST)  
**Date:** Jan 2026

---

## Core Concepts

### 1. The General Solution structure
The solution consists of two parts:
$$y(x) = y_h(x) + y_p(x)$$

* **$y_h$ (Homogeneous Solution):** Solved by setting $r(x) = 0$ (The system's natural behavior).
* **$y_p$ (Particular Solution):** Guessed based on the external force $r(x)$.

### 2. Modification Rule (The "Resonance" Check)
**Crucial Step:** Before calculating coefficients, compare your guessed $y_p$ with $y_h$.

| Condition | Action |
| :--- | :--- |
| **No Match** | Keep the guess as is. |
| **"Crash" (Resonance)** | If a term in $y_p$ matches $y_h$, multiply $y_p$ by **$x$**. |
| **Double Crash** | If it matches a double root in $y_h$, multiply by **$x^2$**. |

---

## Problem Solutions (Pink Highlights)

### Problem 2: Basic Trig (No Resonance)
**ODE:** $$10y'' + 50y' + 57.6y = \cos x$$

1.  **Find $y_h$:**
    * Roots: $\lambda = -1.8, -3.2$
    * $y_h = c_1 e^{-1.8x} + c_2 e^{-3.2x}$
2.  **Find $y_p$:**
    * Guess: $y_p = A \cos x + B \sin x$
    * Result: $A \approx 0.01, B \approx 0.01$
3.  ** Final Answer:**
    $$y = c_1 e^{-1.8x} + c_2 e^{-3.2x} + 0.01 \cos x + 0.01 \sin x$$

---

### Problem 4: Basic Trig (Negative Coeff)
**ODE:** $$y'' - 9y = 18 \cos \pi x$$

1.  **Find $y_h$:**
    * Roots: $\lambda = \pm 3$
    * $y_h = c_1 e^{3x} + c_2 e^{-3x}$
2.  **Find $y_p$:**
    * Guess: $y_p = A \cos \pi x + B \sin \pi x$
    * Solve: $(-\pi^2 - 9)A = 18 \Rightarrow A \approx -0.9539$
3.  ** Final Answer:**
    $$y = c_1 e^{3x} + c_2 e^{-3x} - 0.9539 \cos \pi x$$

---

### Problem 6: The "Boss" Level (Complex Resonance)
**ODE:** $$y'' + y' + (\pi^2 + \frac{1}{4})y = e^{-x/2} \sin \pi x$$

1.  **Find $y_h$:**
    * Roots: $\lambda = -0.5 \pm \pi i$
    * $y_h$ contains $e^{-0.5x} \sin \pi x$. **RESONANCE detected!**
2.  **Find $y_p$:**
    * **Modification:** Multiply guess by **$x$**.
    * Guess: $y_p = x \cdot e^{-0.5x}(A \cos \pi x + B \sin \pi x)$
    * **Professor's Trick (Survivor Formula):**
        $$2 \cdot e^{-0.5x} \cdot \frac{d}{dx}(\text{Trig Part}) = \text{RHS}$$
        $$-2\pi A = 1 \Rightarrow A = -\frac{1}{2\pi}, \quad B = 0$$
3.  ** Final Answer:**
    $$y = e^{-0.5x}(c_1 \cos \pi x + c_2 \sin \pi x) - \frac{x}{2\pi}e^{-0.5x} \cos \pi x$$

---

### Problem 8: Mixed Type (Superposition)
**ODE:** $$3y'' + 27y = 3\cos x + \cos 3x$$
*(Step 0: Divide by 3 $\rightarrow y'' + 9y = \cos x + \frac{1}{3}\cos 3x$)*

1.  **Find $y_h$:**
    * Natural Freq = 3 ($\lambda = \pm 3i$).
2.  **Find $y_p$:**
    * **Part 1 ($\cos x$):** Freq 1 $\neq$ 3. No resonance. $y_{p1} = \frac{1}{8} \cos x$.
    * **Part 2 ($\frac{1}{3}\cos 3x$):** Freq 3 = 3. **Resonance!**
        * Guess: $x(C \cos 3x + E \sin 3x)$
        * Result: $E = 1/18$.
3.  ** Final Answer:**
    $$y = c_1 \cos 3x + c_2 \sin 3x + \frac{1}{8} \cos x + \frac{1}{18} x \sin 3x$$

---

### Problem 10: Calculation Heavy (Table Method)
**ODE:** $$y'' + 2y' + y = 2x \sin x$$

1.  **Find $y_h$:**
    * Roots: $-1, -1$ (Repeated). $y_h = c_1 e^{-x} + c_2 x e^{-x}$.
2.  **Find $y_p$:**
    * Guess: $y_p = (Ax+B)\cos x + (Cx+E)\sin x$
    * Result: $A=-1, C=0, B=1, E=1$.
3.  ** Final Answer:**
    $$y = c_1 e^{-x} + c_2 x e^{-x} - x \cos x + \cos x + \sin x$$

---

### Problem 12: IVP with Resonance
**ODE:** $$y'' + 4y = -12 \sin 2x, \quad y(0)=1.8, y'(0)=5.0$$

1.  **General Solution:**
    * Roots $\pm 2i$. Resonance with $\sin 2x$.
    * Guess: $y_p = x(A \cos 2x + B \sin 2x)$
    * Shortcut: $A = 3, B = 0$.
2.  **Initial Values:**
    * Solve $y(0)$ and $y'(0)$ for constants.
    * $c_1 = 1.8, c_2 = 1$.
3.  ** Final Answer:**
    $$y = 1.8 \cos 2x + \sin 2x + 3x \cos 2x$$

---

### Problem 14: Fake Resonance ("Cancel" Trick)
**ODE:** $$y'' + 4y' + 4y = e^{-2x} \sin 2x, \quad y(0)=1, y'(0)=-1.5$$

1.  **General Solution:**
    * Roots $-2, -2$. RHS has $\sin$. **No Resonance** (Freq mismatch).
    * **Exponential Shift Trick:** LHS is $(D+2)^2$. Let $y_p = e^{-2x}V$.
    * Equation becomes $V'' = \sin 2x \Rightarrow V = -1/4 \sin 2x$.
2.  **Initial Values:**
    * $c_1 = 1, c_2 = 1$.
3.  ** Final Answer:**
    $$y = e^{-2x} + x e^{-2x} - \frac{1}{4} e^{-2x} \sin 2x$$

---

### Problem 16: Mixed IVP
**ODE:** $$y'' - 2y' = 6e^{2x} - 4e^{-2x}, \quad y(0)=-1, y'(0)=6$$

1.  **General Solution:**
    * Roots $0, 2$.
    * Part $6e^{2x}$: Matches root 2. **Resonance.** Guess $Axe^{2x} \rightarrow A=3$.
    * Part $-4e^{-2x}$: No match. Guess $Be^{-2x} \rightarrow B=-0.5$.
2.  **Initial Values:**
    * $c_1 = -1.5, c_2 = 1$.
3.  ** Final Answer:**
    $$y = -1.5 + e^{2x} + 3x e^{2x} - 0.5 e^{-2x}$$

---

## Professor's Cheat Codes

### 1. The Survivor Formula (For Resonance)
Use this when you have **Resonance** (modification $\times x$) and the equation is $y'' + \omega^2 y = F(x)$.
$$2 \cdot (\text{Exponential Part}) \cdot \frac{d}{dx}(y_p \text{'s Trig Part}) = \text{RHS}$$
*(Note: Ensure coefficient of $y''$ is 1)*

### 2. Exponential Shift (For "Perfect Squares")
Use this when LHS is $(D-a)^2 y$ and RHS is $e^{ax} F(x)$.
* Assume $y_p = e^{ax} V(x)$
* Solve simpler equation: $V'' = F(x)$