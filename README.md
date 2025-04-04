# 🧾 SQL Problem: Employee Bonus

**LeetCode Problem**: [Employee Bonus](https://leetcode.com/problems/employee-bonus/)

---

## 📄 Problem Description

### Table: `Employee`

| Column Name | Type    |
|-------------|---------|
| empId       | int     |
| name        | varchar |
| supervisor  | int     |
| salary      | int     |

- `empId` is the unique identifier for each employee.
- Each row provides the employee’s name, ID, salary, and their manager's ID.

---

### Table: `Bonus`

| Column Name | Type |
|-------------|------|
| empId       | int  |
| bonus       | int  |

- `empId` is a foreign key referencing `Employee.empId`.
- Each row shows the bonus an employee received.

---

## 🎯 Objective

Write a SQL query to **return the name and bonus amount** of each employee who has **a bonus less than 1000** or **no bonus at all**.

Return the result in **any order**.

---

## 🧪 Example

### Input

#### `Employee` Table:

| empId | name   | supervisor | salary |
|-------|--------|------------|--------|
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |

#### `Bonus` Table:

| empId | bonus |
|-------|-------|
| 2     | 500   |
| 4     | 2000  |

### Output

| name | bonus |
|------|-------|
| Brad | null  |
| John | null  |
| Dan  | 500   |

---

## ✅ SQL Solution

```sql
SELECT 
    E.name, 
    B.bonus 
FROM 
    Employee E
LEFT JOIN 
    Bonus B 
ON 
    E.empId = B.empId
WHERE 
    B.bonus < 1000 OR B.bonus IS NULL;
```

---

## 🧠 Key Concepts

- `LEFT JOIN` to include employees even if they don’t have a bonus.
- Filtering with `WHERE` to get bonuses less than 1000 or `NULL`.
- `IS NULL` to capture employees with no bonus entry at all.

---

✍️ *Contributed by Deepak Shanmugam K  
📘 *SQL | LeetCode Practice*
