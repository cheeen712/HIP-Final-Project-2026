# Concert Ticket Booking System - Fitts' Law HCI Experiment

An interactive Human-Computer Interaction (HCI) experiment platform built with HTML5, Tailwind CSS, Chart.js, and Web Audio API. This project evaluates human pointing performance in high-pressure UI scenarios (e.g., rush-buying concert tickets) using Fitts' Law (ISO 9241-9 standard) with Welford's effective width correction.

---

## 1. Scenario & User Context

* **Target Users:** Concertgoers, general consumers navigating anti-scalping mechanisms, and users performing rapid visual/motor interaction tasks.
* **Context of Use:** **"High-Stakes Live Ticket Drop (T0 Launch)"**. Users operate under intense pressure, tight time constraints, and heightened physiological stress (e.g., elevated heart rate, minor hand tremors, and rapid visual search).
* **Core Task:** Users must complete a 3-step rapid-pointing sequence: **"Lock Ticket $\rightarrow$ Select Seat $\rightarrow$ Confirm Payment"** within seconds while maintaining high speed and accuracy under the Speed-Accuracy Trade-off.

---

## 2. Real-World HCI Problem

Traditional ticketing websites often suffer from significant UX/HCI flaws during high-concurrency ticket drops:

* **High-Stress Misclicks & Accidental Actions:** High-risk actions (e.g., *Cancel Order*, *Back*, or *Clear Selection*) are frequently placed near critical confirmation buttons with similar visual sizes. Under pressure, slight motor deviations cause accidental clicks, resetting the process and causing severe user frustration.
* **Cognitive Overload & Context Switching Across Pages:** Multi-page checkout flows destroy spatial memory every time a page reloads. Users' eyes must re-orient to locate the next target, significantly increasing Movement Time ($MT$).
* **Suboptimal Target Scale & Spatial Distribution:** Interfaces fail to tailor button dimensions ($W$) and distances ($A$) to the tolerance level of each specific step, causing both movement time and error rates to spike simultaneously.

---

## 3. Innovations & Fitts' Law Application

This dashboard adopts a **Single-Page Dashboard (SPD)** design and dynamically adjusts the Index of Difficulty ($ID$) based on the Shannon Formulation (ISO 9241-9) with Welford's Angle-of-Approach Correction ($W'$):

$$ID = \log_2\left(\frac{A}{W'} + 1\right)$$

### Key Interface Adaptations

* **Step 1: Ticket Selection (Zone A) — Low $ID$ (Zero Delay)**
  * **Design:** Large target width ($W$) positioned near the initial Start Anchor (small distance $A$).
  * **Fitts' Law Context:** Low $ID$ ($\approx 1.5 - 2.0\text{ bits}$). Prioritizes raw motor speed over fine precision, allowing users to hit the target via muscle memory without fine visual alignment ($MT$ minimization).

* **Step 2: Seat Grid Selection (Zone B) — High $ID$ (High Precision)**
  * **Design:** Small circular seat grid nodes (small $W$) located at medium-to-far distances (large $A$).
  * **Fitts' Law Context:** High $ID$ ($\approx 3.5 - 5.0\text{ bits}$). Forces the user's oculomotor system into a feedback-guided correction phase, minimizing accidental selections of adjacent seats.

* **Step 3: Payment Confirmation (Zone C) — Medium $ID$ (Accidental-Click Prevention)**
  * **Design:** Moderate-width rectangular target positioned in the right-hand corner.
  * **Fitts' Law Context:** Medium $ID$ ($\approx 2.5 - 3.5\text{ bits}$). Spatially separated from Zone B to prevent misclicks while leveraging the Infinite Edge Effect of the viewport corner to speed up terminal targeting.

* **Pre-cueing Visual Anchor:**
  * When hovering or clicking the Start Anchor, the system renders a **Ghost Preview** (dashed outline) over the upcoming target. This allows users to initiate saccadic eye movements in advance, reducing cognitive reaction time before motor execution.

---

## 4. Mathematical Model & Empirical Results

The platform evaluates performance based on linear regression modeling:

$$MT = a + b \cdot ID$$

* **Movement Time ($MT$):** Time elapsed between the previous click and target acquisition (in milliseconds).
* **Throughput ($TP$):** Calculated as $TP = \frac{ID}{MT}$ (in bits/second).
* **Target Fitness ($R^2$):** Experimental trials demonstrate strong linear correlation ($R^2 > 0.85$), validating the predictive accuracy of Fitts' Law under the provided UI layout.

---

## 5. Getting Started

1. **Clone or download this repository:**
   ```bash
   git clone https://github.com/your-username/fitts-law-ticket-booking.git
   cd fitts-law-ticket-booking
   ```

2. **Open the interface:**
   Launch `index.html` in any modern web browser (Google Chrome, Firefox, Safari, Edge).

3. **Run the experiment:**
   * Click **"開始實驗 (含練習 round)"** to launch the test.
   * Complete 3 practice rounds followed by 15 formal test trials.
   * View real-time linear regression plots ($R^2$, $MT$ vs $ID$), step metrics, or export the raw dataset as a CSV file.

---

## 6. Live Demo & Video Demonstration

* **Live GitHub Pages Demo:** [https://your-username.github.io/fitts-law-ticket-booking/](https://your-username.github.io/fitts-law-ticket-booking/)
* **Video Walkthrough (YouTube):** [Insert YouTube / Vimeo Video Link Here]

---

## 7. Tech Stack

* **Frontend:** HTML5, Tailwind CSS
* **Chart Library:** Chart.js
* **Iconography:** FontAwesome 6
* **Audio Feedback:** Web Audio API
