# Engineering Mathematics Review: Section 2.10
## Solution by Variation of Parameters

### 1. Core Concepts
This section deals with solving **Second-Order Non-Homogeneous Linear ODEs**:
$$y'' + p(x)y' + q(x)y = r(x)$$

#### Method Selection Strategy
* **Method of Undetermined Coefficients (MUC):**
    * **Use when:** $r(x)$ is a polynomial, exponential ($e^{kx}$), sine, cosine, or a sum/product of these.
    * **Pros:** Faster, algebraic.
    * **Cons:** Cannot handle other functions (like $\tan x$, $1/x$).
    * **Warning:** Watch out for "Resonance" (Duplication with $y_h$). Multiply by $x$ or $x^2$ if needed.

* **Method of Variation of Parameters (MVP):**
    * **Use when:** $r(x)$ involves $\sec x, \csc x, \tan x, \cot x, \ln x$, or reciprocal functions like $\frac{1}{x}, \frac{1}{x^2+1}$.
    * **Pros:** General method (works for any $r(x)$).
    * **Cons:** Requires calculating integrals, which can be complex.

---

### 2. Variation of Parameters: Standard Operating Procedure (SOP)

#### Step 1: Find the Homogeneous Solution ($y_h$)
Solve the auxiliary equation for $y'' + p(x)y' + q(x)y = 0$.
$$y_h = c_1 y_1 + c_2 y_2$$

#### Step 2: Calculate the Wronskian ($W$)
$$W(y_1, y_2) = \begin{vmatrix} y_1 & y_2 \\ y_1' & y_2' \end{vmatrix} = y_1 y_2' - y_2 y_1'$$

#### Step 3: Find the Particular Solution ($y_p$)
Use the formula:
$$y_p = -y_1 \int \frac{y_2 r(x)}{W} dx + y_2 \int \frac{y_1 r(x)}{W} dx$$

> **Note:** Ensure the coefficient of $y''$ is **1** before identifying $r(x)$.

#### Step 4: General Solution
$$y = y_h + y_p$$

---

### 3. Essential Integral Formulas for this Section
You will frequently encounter these integrals in MVP problems:
* $\int \tan x \, dx = \ln|\sec x|$
* $\int \cot x \, dx = \ln|\sin x|$
* $\int \sec x \, dx = \ln|\sec x + \tan x|$
* $\int \csc x \, dx = \ln|\csc x - \cot x|$
* $\int \sec^2 x \, dx = \tan x$
* $\int \csc^2 x \, dx = -\cot x$
* $\int \frac{1}{x^2 + a^2} \, dx = \frac{1}{a} \tan^{-1}(\frac{x}{a})$

---

### 4. Selected Practice Problems (Pink-Marked)

These are the key problems identified from the textbook problem set.

#### Problem 2
**ODE:** $y'' + 9y = \csc 3x$
* **Type:** MVP (due to $\csc$)
* **Key Step:** $\int \cot 3x \, dx = \frac{1}{3}\ln|\sin 3x|$
* **Solution:**
    $$y = c_1 \cos 3x + c_2 \sin 3x - \frac{1}{3}x \cos 3x + \frac{1}{9} \sin 3x \ln|\sin 3x|$$

#### Problem 4
**ODE:** $y'' - 4y' + 5y = e^{2x} \csc x$
* **Type:** MVP (due to $\csc$)
* **Key Step:** $W$ calculation involves cancellations of exponentials.
* **Solution:**
    $$y = e^{2x}(c_1 \cos x + c_2 \sin x) - x e^{2x} \cos x + e^{2x} \sin x \ln|\sin x|$$

#### Problem 6
**ODE:** $(D^2 + 6D + 9I)y = \frac{16e^{-3x}}{x^2 + 1}$
* **Type:** MVP (due to denominator variable)
* **Key Step:** Homogeneous solution has repeated roots ($e^{-3x}, xe^{-3x}$). Integral involves $\tan^{-1}x$.
* **Solution:**
    $$y = e^{-3x}(c_1 + c_2 x) - 8e^{-3x}\ln(x^2+1) + 16xe^{-3x}\tan^{-1}x$$

#### Problem 8
**ODE:** $(D^2 + 4I)y = \cosh 2x$
* **Type:** **MUC Recommended** (Shortcut)
* **Hint:** Convert $\cosh 2x$ to $\frac{1}{2}(e^{2x} + e^{-2x})$.
* **Warning:** Check for resonance (none here). Coefficients are $1/8$.
* **Solution:**
    $$y = c_1 \cos 2x + c_2 \sin 2x + \frac{1}{8} \cosh 2x$$

#### Problem 10
**ODE:** $(D^2 + 2D + 2I)y = 4e^{-x} \sec^3 x$
* **Type:** MVP (due to $\sec^3$)
* **Key Step:** Integral of $\tan x \sec^2 x$ uses u-substitution ($u=\tan x$).
* **Solution:**
    $$y = e^{-x}(c_1 \cos x + c_2 \sin x) + 2e^{-x} \sec x$$

#### Problem 12
**ODE:** $(D^2 - I)y = \frac{1}{\cosh x}$
* **Type:** MVP (Reciprocal function)
* **Key Step:**
    To integrate $\int \frac{1}{e^{2x}+1} dx$, multiply numerator and denominator by $e^{-2x}$ or use partial fractions.
* **Solution:**
    $$y = c_1 e^x + c_2 e^{-x} + x e^x - \cosh x \ln(e^{2x} + 1)$$

---
*Created for Engineering Mathematics Review.*
