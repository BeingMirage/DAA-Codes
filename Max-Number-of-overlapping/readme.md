# Activity Selection Problem 🧩

## 📘 Overview
The **Activity Selection Problem** is a classic example of the **Greedy Algorithm** strategy.  
The goal is to select the **maximum number of non-overlapping activities** that can be performed by a single person or machine.

Each activity has:
- A **start time**
- A **finish time**

We can perform an activity only if it starts **after or when** the previous activity ends.

---

## ⚙️ Algorithm Logic

### Greedy Choice
Always select the **activity that finishes earliest** among the remaining ones that start after or when the last selected activity ends.  
This ensures there’s **maximum time left** for upcoming activities.

### Steps
1. Sort all activities based on their **finish time** (ascending order).  
2. Select the first activity (it ends the earliest).  
3. For every next activity:
   - If its **start time ≥ finish time** of the last selected activity, select it.  
4. Continue until all activities are checked.

---

## 🧠 Example

| Activity | Start | Finish |
|-----------|--------|--------|
| A1 | 1 | 2 |
| A2 | 3 | 4 |
| A3 | 0 | 6 |
| A4 | 5 | 7 |
| A5 | 8 | 9 |
| A6 | 5 | 9 |

**Sorted by finish time:**
A1(1–2), A2(3–4), A4(5–7), A5(8–9)

✅ **Selected Activities:** A1, A2, A4, A5  
Total = **4 activities**

---

## 💻 Python Code

```python
def activity_selection(start, finish):
    # Combine start and finish times and sort by finish time
    activities = sorted(zip(start, finish), key=lambda x: x[1])

    selected = []
    last_end = 0

    for s, f in activities:
        if s >= last_end:
            selected.append((s, f))
            last_end = f

    return selected


# Example usage
start = [1, 3, 0, 5, 8, 5]
finish = [2, 4, 6, 7, 9, 9]

print("Selected activities:", activity_selection(start, finish))
