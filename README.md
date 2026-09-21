
# Concert Ticket Booking System - Fitts' Law HCI Experiment

An interactive Human-Computer Interaction (HCI) experiment that applies **Fitts' Law** to a simulated concert ticket booking scenario. The system evaluates pointing performance under different target sizes and movement distances through a three-stage ticket-booking task.

The experiment is implemented as a single-page web application using **HTML5, Tailwind CSS, JavaScript, Chart.js, and Web Audio API**.

---

## Overview

Concert ticket sales often require users to complete multiple time-sensitive interactions in a short period of time. In such scenarios, small targets, long cursor movements, and rapid task transitions may increase the likelihood of misclicks and longer movement times.

This project simulates a high-pressure ticket-booking interaction and uses **Fitts' Law** to investigate the relationship between:

* Target size
* Movement distance
* Index of Difficulty (ID)
* Movement Time (MT)
* Pointing performance
* Selection errors

The experiment consists of three sequential task stages:

> **Lock Ticket → Select Seat → Confirm Payment**

Each stage contains different target configurations designed to produce different levels of pointing difficulty.

---

## 1. Research Context

### Scenario

The experiment simulates a time-sensitive concert ticket booking process. Participants must rapidly interact with interface elements representing common ticket-purchasing actions.

The scenario is designed to resemble the interaction pressure users may experience during a highly competitive concert ticket release.

### HCI Problems

The experiment focuses on several common pointing and interaction problems:

* **Small target size:** Smaller buttons require greater pointing precision.
* **Movement distance:** Targets positioned farther from the current cursor location require longer movements.
* **Target difficulty:** Different combinations of target size and movement distance produce different levels of Index of Difficulty.
* **Selection errors:** Clicking outside the target is recorded as a miss.
* **Sequential interaction:** Users must complete multiple pointing actions in succession.

---

## 2. Research Question

The experiment investigates the following question:

> **How does the difficulty of a pointing task affect users' movement time and selection performance in a simulated concert ticket-booking interface?**

Based on Fitts' Law, tasks with a higher Index of Difficulty are expected to require more movement time.

---

## 3. Experimental Design

### 3.1 Task Flow

Participants complete three sequential task stages:

| Stage  | Task            | Purpose                                                               |
| ------ | --------------- | --------------------------------------------------------------------- |
| Step 1 | Lock Ticket     | Simulates the initial ticket-locking interaction                      |
| Step 2 | Select Seat     | Simulates selecting a seat from a more difficult target configuration |
| Step 3 | Confirm Payment | Simulates the final confirmation action                               |

The experiment therefore contains:

**15 formal trials × 3 task stages = 45 target acquisitions**

---

### 3.2 Practice Trials

Before the formal experiment begins, participants complete:

* **3 practice trials**
* Practice data are excluded from the formal performance analysis.

Practice trials allow participants to become familiar with the interaction mechanism and target-selection task before data collection begins.

---

### 3.3 Target Conditions

The experiment uses **pre-designed target configurations** with different combinations of:

* Target position
* Target width
* Target height
* Movement distance

These configurations are designed to produce relatively different levels of pointing difficulty across the three task stages.

The actual Index of Difficulty is calculated from the geometry of each target acquisition rather than being manually assigned.

---

## 4. Fitts' Law Model

The experiment uses the Shannon formulation of Fitts' Law:

$$
ID = \log_2\left(\frac{A}{W'} + 1\right)
$$

where:

* **ID** = Index of Difficulty
* **A** = Movement amplitude, representing the distance between the previous and current target
* **W′** = Effective target width

The basic Fitts' Law relationship is modeled as:

$$
MT = a + b(ID)
$$

where:

* **MT** = Movement Time
* **a** = Regression intercept
* **b** = Regression slope

The experiment evaluates whether the collected pointing data exhibit the expected relationship between movement time and task difficulty.

---

## 5. Effective Target Width

For rectangular targets, the implementation applies an **angle-of-approach correction** based on the movement direction to estimate the effective target width used in the ID calculation.

Circular targets use their diameter as the effective width.

Therefore, the width used in the Fitts' Law calculation is not always simply the visual width or height of the target.

This correction allows the experiment to account for the direction from which a rectangular target is approached.

---

## 6. Movement Time

Movement Time is measured from the beginning of a formal target acquisition until the participant successfully selects the target.

Missed clicks are recorded separately and do not immediately complete the trial.

The system records the successful acquisition time together with the target geometry and calculated difficulty.

---

## 7. Throughput

The experiment calculates nominal pointing throughput using:

$$
TP = \frac{ID}{MT_{sec}}
$$

where:

* **TP** = Throughput
* **ID** = Index of Difficulty
* **MT<sub>sec</sub>** = Movement Time in seconds

The results interface reports performance metrics for the collected target acquisitions.

---

## 8. Error Measurement

The system records clicks that occur outside the active target as **misses**.

Misses are used to evaluate selection accuracy and provide additional information about pointing performance.

The interface also provides visual and audio feedback during interaction.

---

## 9. Pre-Cueing and Target Preview

Before each target acquisition, the interface displays a **dashed ghost preview** indicating the location of the upcoming target.

This preview provides participants with advance visual information about the next target location, allowing them to visually prepare for the upcoming pointing movement.

The preview is intentionally included as part of the experimental interface and should be considered when interpreting the results, since pre-cueing may influence pointing behavior.

---

## 10. Data Collection

For each successful target acquisition, the system records information including:

* Task stage
* Trial number
* Target position
* Target width
* Target height
* Movement amplitude
* Effective target width
* Index of Difficulty
* Movement Time
* Throughput
* Error/miss information

The collected data can be exported as a CSV file for further analysis.

---

## 11. Performance Analysis

After the formal experiment is completed, the system performs a linear regression between:

* **Independent variable:** Index of Difficulty (ID)
* **Dependent variable:** Movement Time (MT)

The resulting regression is represented as:

$$
MT = a + b(ID)
$$

The results interface displays:

* Regression line
* Regression equation
* R² value
* Overall performance metrics
* Step-level performance information

### R²

The coefficient of determination (**R²**) is calculated from the collected experimental data and reported after the experiment.

Rather than assuming a predetermined R² value, the experiment uses the observed data to evaluate how well the linear Fitts' Law model describes the collected movement-time measurements.

---

## 12. Results Visualization

The results dashboard provides a post-experiment visualization of the collected data.

The interface includes:

* **Movement Time vs. Index of Difficulty**
* Linear regression line
* R² value
* Step-level statistics
* Overall pointing performance
* Data export functionality

This allows participants or researchers to inspect the relationship between task difficulty and movement time after completing the experiment.

---

## 13. Getting Started

### Clone the Repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### Run the Experiment

No backend server is required.

Simply open the HTML file in a modern web browser:

```text
index.html
```

The experiment runs entirely on the client side.

---

## 14. Experimental Procedure

1. Open the experiment in a web browser.
2. Read the experimental instructions.
3. Complete **3 practice trials**.
4. Begin the formal experiment.
5. Complete the three task stages sequentially:

   * Lock Ticket
   * Select Seat
   * Confirm Payment
6. Complete all **45 formal target acquisitions**.
7. View the results dashboard.
8. Inspect the regression analysis and performance metrics.
9. Export the collected data as a CSV file if needed.

---

## 15. Output

After completing the experiment, the system provides:

### Performance Metrics

* Total movement time
* Average movement time
* Throughput
* Error/miss information
* Step-level performance

### Regression Analysis

* Fitts' Law regression equation
* Regression slope
* Regression intercept
* R²

### Data Export

Experimental data can be exported as a `.csv` file for external analysis using tools such as:

* Microsoft Excel
* Google Sheets
* Python
* R
* MATLAB

---

## 16. Technology Stack

| Technology             | Purpose                                                 |
| ---------------------- | ------------------------------------------------------- |
| **HTML5**              | Page structure and experimental interface               |
| **CSS / Tailwind CSS** | Interface styling and responsive layout                 |
| **JavaScript**         | Experiment logic, timing, data collection, and analysis |
| **Chart.js**           | Regression and performance visualization                |
| **Font Awesome 6**     | Interface icons                                         |
| **Web Audio API**      | Interaction feedback sounds                             |

---

## 17. Project Structure

```text
.
├── index.html
├── README.md
└── assets/
    └── ...
```

The main experiment logic is implemented directly within the HTML/JavaScript application.

---

## 18. Limitations

Several limitations should be considered when interpreting the experimental results.

### 18.1 No Physiological Measurements

Although the scenario represents a time-sensitive ticket-booking environment, the current implementation does **not** directly measure physiological stress.

For example, it does not collect:

* Heart rate
* Skin conductance
* EEG
* Tremor
* Stress questionnaires

Therefore, the experiment should be interpreted as a **simulated high-pressure interaction scenario**, rather than a physiological stress experiment.

### 18.2 Pre-Cueing Effect

The dashed target preview provides advance information about the upcoming target location.

This may affect participants' visual preparation and pointing behavior and should therefore be considered when interpreting movement-time results.

### 18.3 Pre-Designed Target Configurations

The experiment uses predefined target configurations rather than directly specifying an exact ID value for every trial.

The actual ID is calculated from the resulting movement amplitude and effective target width.

### 18.4 Effective Width Estimation

The effective width correction is based on target geometry and movement direction.

It should not be interpreted as an empirical effective width estimated from the statistical distribution of endpoint coordinates.

### 18.5 Nominal Throughput

The reported throughput is calculated from the task's ID and measured movement time.

It should therefore be treated as the experiment's calculated or **nominal throughput**, rather than a full throughput estimate based on a larger endpoint-distribution analysis.

### 18.6 Sample Size

The current experiment records a limited number of target acquisitions within a single experimental run.

Therefore, the results should primarily be interpreted as observations from the collected experimental session rather than as universal conclusions about human pointing performance.

---

## 19. Live Demo

**Demo:**
`<your-github-pages-url>`

> Replace the placeholder above with the actual GitHub Pages deployment URL.

---

## 20. Video Demonstration

**Demo Video:**
`<your-video-url>`

The demonstration video can be used to show:

* Experimental instructions
* Practice trials
* Formal trials
* Target interactions
* Results dashboard
* Regression visualization
* CSV data export

---

## 21. Key Takeaways

This project demonstrates how Fitts' Law can be incorporated into an interactive web-based HCI experiment.

The system connects theoretical pointing models with a practical interaction scenario by:

* Designing target configurations with different pointing difficulties
* Measuring movement time
* Recording selection errors
* Calculating Index of Difficulty
* Applying effective-width correction
* Modeling the MT–ID relationship using linear regression
* Calculating nominal throughput
* Visualizing experimental results
* Exporting experimental data for further analysis

The project provides a self-contained environment for studying the relationship between **target geometry, pointing difficulty, and movement performance** in a simulated concert ticket-booking interface.
