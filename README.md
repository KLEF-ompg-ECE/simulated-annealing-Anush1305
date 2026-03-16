# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** ANUSH THAK
**Student ID    :** 2310040029
**Date Submitted:** 16/03/26 

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**


`count_clashes()` measures the total number of exam conflicts for all students, where a conflict means a student has two exams scheduled in the same time slot. A value of 0 means a perfect timetable with no clashes.


**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**


`generate_neighbor()` creates a new timetable by moving one randomly chosen exam to a different slot. The new timetable differs from the current one by only one exam's slot assignment, allowing small changes for exploration.


**Q3. In `run_sa()`, there is this line:**

if delta < 0 or random.random() < math.exp(-delta / T):

**What does this line decide? Why does SA sometimes accept a worse solution?**

This line decides whether to accept the new timetable. It always accepts improvements (when delta < 0), but sometimes accepts worse solutions based on the temperature and probability. This helps the algorithm escape local minima and explore more possibilities, which is essential for finding better solutions in complex optimization problems.


---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**


| Metric | Your result |
|--------|-------------|
| Number of iterations completed | 1379 |
| Clashes at iteration 1 | 12 |
| Final best clashes | 3 |
| Did SA reach 0 clashes? (Yes / No) | No |

**Copy the printed timetable output here:**
```
	Final Timetable
------------------------------------------
	Slot 1:  Geography
	Slot 2:  Chemistry, English
	Slot 3:  History, Computer Science, Economics
	Slot 4:  Biology, Statistics
	Slot 5:  Mathematics, Physics
------------------------------------------
	Total clashes : 3
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**
The plot shows a rapid drop in clashes at the beginning, followed by a gradual flattening as the algorithm converges. The biggest drop happens in the early iterations, and the curve becomes nearly flat as it approaches the best solution found.
---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

```
| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        | 8             | 31                   | No                 |
| 0.95        | 3             | 135                  | No                 |
| 0.995       | 3             | 1379                 | No                 |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result?**
With fast cooling (0.80), the temperature drops quickly and the algorithm stops early, resulting in a higher number of clashes. Slower cooling rates (0.95 and 0.995) allow more iterations and better exploration, leading to fewer clashes. The slowest cooling rate (0.995) takes the longest but achieves the same best result as 0.95, showing that thorough search improves solution quality.

**Which cooling_rate gave the best result? Why do you think that is?**
Both 0.95 and 0.995 gave the best result of 3 clashes, but 0.995 required more iterations. The best result comes from slower cooling because it allows the algorithm to explore more solutions and avoid getting stuck in poor local minima.
---

## Summary

**Complete this table with your best result from each experiment:**


| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 | 3 | Slow cooling allows thorough search and fewer clashes. |
| 2 — Cooling rate | cooling_rate = 0.95 | 3 | Moderate cooling balances speed and solution quality. |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments?**
Simulated Annealing is effective for solving scheduling problems by allowing occasional acceptance of worse solutions to escape local minima. The cooling rate is crucial: fast cooling leads to quick but suboptimal results, while slow cooling improves solution quality at the cost of more computation. The most important lesson is that patience and thorough exploration are key to finding better solutions in complex optimization problems.
---

## Submission Checklist

 - [x] Student name and ID filled in
 - [x] Q1, Q2, Q3 answered
 - [x] Experiment 1: table filled, timetable pasted, plot observation written
 - [x] Experiment 2: results table filled (3 rows), observation and answer written
 - [x] Summary table completed and reflection written
-  [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
