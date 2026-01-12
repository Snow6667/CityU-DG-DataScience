NOTE: The university policy on academic dishonesty and plagiarism (cheating) will be taken very seriously in this course. Everything submitted should be your own writing or coding. You must not let other students copy your work. Discussions of the assignment are okay, e.g. understanding the concepts involved. This assignment is an individual one. Upload your work as a single archive file with name `A2-XXXX-YYYY.zip` where `XXXX` is your name and `YYYY` is your student ID. Remember to include all files in the archive file.

---

# Part I. Relational Algebra (35 points)

Consider the following relational schema.

- Emp(eid: integer, ename: string, age: integer, salary: real)
- Works(eid: integer, did: integer, pct_time: integer)
- Dept(did: integer, dname: string, budget: real, managerid: integer)

Write the following queries in relational algebra.

- **(a)** Print the names and ages of each employee who works in both the Hardware department and the Software department. (7 points)
- **(b)** Print the name of each employee whose salary exceeds the budget of all the departments that he or she works in. To illustrate, if the employee works in 3 departments, whose budgets are 1000, 2000 and 3000 respectively, then the maximum budget of all the departments that he/she works in is 3000. (7 points)
- **(c)** Find the `ename`, `age` of managers who manage only departments with budgets greater than $1 million. (7 points)
- **(d)** Find the `ename`s of managers who manage the departments with the greatest budgets. To illustrate, suppose there are three departments like this: department 1 with a budget of $1 million, department 2 with a budget of $2 million, department 3 with a budget of $2 million. Then departments 2 and 3 have the greatest budgets. (14 points)

---

# Part II. SQL Queries (40 points)

Copy all SQL queries into one SQL file called `part2.sql`. For each query, please provide the comment as `-- part2a` for the first query.

All screenshots should be submitted together as a single PDF file called `part2.pdf`.

Upload your submissions as a single archive file called `part2.zip`.

Consider the relational schema for company in Part I, write SQL queries for each request in Part I and one extra request in the following. Your queries should be executable in SQLite.

In this part, you also need to use the `A2.db` (please download `A2.db` from course files) database in DB Browser for SQLite to give a screenshot for each query’s result.

- **(a)** 8 points
- **(b)** 6 points
- **(c)** 7 points
- **(d)** 9 points
- **(e)** For each department with more than 20 full-time-equivalent employees (i.e., the total `pct_time` of the part-time and full-time employees add up to at least 2000 hrs, assuming that the `pct_time` of a full-time employee is 100 hrs), print the `did` together with the number of employees that work in that department. (10 points)

---

# Part III. Design Theory (25 points)

Suppose we have a relation schema `R(A1, A2, A3, A4)` with Functional Dependencies (FDs):

1. `A3 → A1`
2. `A4 → A2`
3. `A1, A2 → A3`
4. `A1, A2 → A4`

Answer the following:

1. **Candidate keys** (6 points)  
   List all candidate keys of R.

2. **BCNF main requirement** (6 points)  
   The main requirement for BCNF means that the left-hand side of an FD is a superkey. Do any FDs listed above violate the main requirement? Please explain for each FD.

3. **3NF secondary requirement** (4 points)  
   The secondary requirement for 3NF means that for an FD `X → Y`, `Y` is a part of a candidate key. Do any FDs listed above violate the secondary requirement? Please explain for each FD.

4. **BCNF decomposition** (9 points)  
   Give a BCNF decomposition of R that is lossless and has as few tables as possible.
