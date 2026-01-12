# Assignment 3

## Part I. Storage and Indexing (45 points)

Consider the following instance of the `Students` relation, sorted by `age`.

`(sid, name, login, age, gpa)`

| sid   | name    | login        | age | gpa |
|-------|---------|--------------|-----|-----|
| 53831 | Madayan | madayan@music| 11  | 1.8 |
| 53832 | Guldu   | guldu@music  | 12  | 2.0 |
| 53666 | Jones   | jones@cs     | 18  | 3.4 |
| 53688 | Smith   | smith@ee     | 19  | 3.2 |
| 53650 | Smith   | smith@math   | 19  | 3.8 |

For the purposes of this question, assume that these tuples are stored in a sorted file in the order shown. Each page can store up to three data records. So the first three tuples are on page 1, the fourth is on page 2 etc.

Explain what the data entries in each of the following indexes contain. If the order of entries is significant (which means such order is the same as the order of tuples in the data files), say so and explain why. If such an index cannot be constructed, say so, and explain why.

- **(5 points)** An unclustered index on `age` using Alternative (1).
- **(5 points)** An unclustered index on `age` using Alternative (2).
- **(5 points)** An unclustered index on `age` using Alternative (3).
- **(5 points)** An unclustered index on `gpa` using Alternative (1).
- **(5 points)** An unclustered index on `gpa` using Alternative (2).
- **(5 points)** An unclustered index on `gpa` using Alternative (3).
- **(5 points)** A clustered index on `gpa` using Alternative (1).
- **(5 points)** A clustered index on `gpa` using Alternative (2).
- **(5 points)** A clustered index on `gpa` using Alternative (3).

For Alternative (2), use the notation `<A, (B,C)>` where `A` is the search key for the entry and `(B,C)` is the rid for data entry, with `B` being the page number of the entry and `C` being the location on page `B` of the entry. For Alternative (3), the notation of rid is the same, and an entry is `<A, L>` where `L` is a list of rid’s.

---

## Part II. Query Evaluation (30 points)

1. **(18 points)** Consider the following SQL query.

```sql
SELECT S.sname
FROM Sailors S, Reserves R, Boats B
WHERE S.sid = R.sid AND R.bid = B.bid AND B.colour = 'red'
INTERSECT
SELECT S.sname
FROM Sailors S, Reserves R, Boats B
WHERE S.sid = R.sid AND R.bid = B.bid AND B.colour = 'green';
```

Write a query evaluation plan (relational algebra tree) for evaluating this query. (You don’t have to annotate the nodes with access methods, just specify the relational operator for each node.)

2. **(12 points)** Consider the following schema with the `Sailors` relation:

```sql
Sailors(sid: integer, sname: string, rating: integer, age: real)
```

For each of the following indexes, list whether the index matches the given selection conditions and explain why.

- A hash index on the search key `<Sailors.sid, Sailors.age>`
  - `age = 21 AND sid = 50,000 (Sailors)`
  - `age < 21 AND sid = 50,000 (Sailors)`

- A B+-tree on the search key `<Sailors.sid, Sailors.age>`
  - `sid < 50,000 AND age = 21 (Sailors)`
  - `age > 21 AND sid = 50,000 (Sailors)`
  - `sid > 50,000 (Sailors)`
  - `age < 21 (Sailors)`

---

## Part III. Map-Reduce (25 points)

Design a Map-Reduce algorithm to compute matrix multiplication $C = AB$ where $A \in \mathbb{R}^{M \times K}$ and $B \in \mathbb{R}^{K \times N}$. Suppose the input is a collection of key-value pairs in the form

- $(\text{null}, (A, i, j, A_{ij}))$ or
- $(\text{null}, (B, i, j, B_{ij}))$,

where the 4-tuple $(A, i, j, A_{ij})$ indicates that the entry at the $i$-th row and the $j$-th column of the matrix $A$ is of value $A_{ij}$.

The final output matrix is also a collection of key-value pairs in the form

- $(\text{null}, (C, i, j, C_{ij}))$.
