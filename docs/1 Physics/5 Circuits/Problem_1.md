# Problem 1


---

$$
\textbf{🔹 Understanding Equivalent Resistance}
$$

$$
\text{Equivalent resistance depends on how resistors are arranged in a circuit:}
$$

---

$$
\textbf{1️⃣ Series Resistors}
$$

$$
\text{Resistors are in series if the same current flows through them one after another.}
$$

$$
R_{eq} = R_1 + R_2 + \dots + R_n
$$

$$
\textbf{Example:} \text{ If three resistors } (R_1 = 5\Omega, R_2 = 10\Omega, R_3 = 20\Omega) 
\text{ are connected in series,
 the total resistance is:}
$$

$$
R_{eq} = 5 + 10 + 20 = 35\Omega
$$

---

$$
\textbf{2️⃣ Parallel Resistors}
$$

$$
\text{Resistors are in parallel if they share the same voltage drop but split the current.}
$$

$$
\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
$$

$$
\textbf{Example:} \text{ If two resistors } (R_1 = 6\Omega, R_2 = 3\Omega) \text{ are in parallel, their equivalent resistance is:}
$$

$$
\frac{1}{R_{eq}} = \frac{1}{6} + \frac{1}{3} = \frac{1}{2} \Rightarrow R_{eq} = 2\Omega
$$

---

$$
\textbf{3️⃣ Complex Networks}
$$

$$
\text{Real-world circuits often involve nested combinations of series and parallel resistors.}
$$

$$
\begin{aligned}
&\bullet \ \textbf{Traditional approach:} \text{ Manually apply the rules iteratively.} \\
&\bullet \ \textbf{Graph theory approach:} \text{ Treat the circuit as a graph, making automated reductions possible.} \\
\end{aligned}
$$

---

$$
\textbf{🔹 Graph Representation of Electrical Circuits}
$$

$$
\text{A circuit can be represented as a graph, where:}
$$

$$
\begin{aligned}
&\bullet \ \textbf{Nodes (vertices)} \text{ represent junctions or connection points.} \\
&\bullet \ \textbf{Edges} \text{ represent resistors, and their weights correspond to resistance values.} \\
\end{aligned}
$$

$$
\text{Using graph algorithms, we can systematically reduce complex circuits.}
$$

---

$$
\textbf{🔹 Algorithm for Equivalent Resistance Calculation}
$$

$$
\text{The approach follows three key steps:}
$$

---

$$
\textbf{Step 1: Graph Representation}
$$

$$
\text{Construct a graph } G(V,E) \text{ where:}
$$

$$
\begin{aligned}
&V \text{ is the set of nodes (junctions).} \\
&E \text{ is the set of edges (resistors).} \\
\end{aligned}
$$

$$
\text{Each resistor } R_i \text{ between nodes } A \text{ and } B \text{ is represented as an edge:}
$$

$$
(A,B,R_i)
$$

---

$$
\textbf{Step 2: Identify Series and Parallel Resistors}
$$

$$
\textbf{Series Reduction:} \text{ If a node has only two neighbors, merge it and sum the resistances:}
$$

$$
R_{eq} = R_1 + R_2
$$

$$
\textbf{Parallel Reduction:} \text{ If multiple edges connect the same two nodes, apply:}
$$

$$
\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
$$

---

$$
\textbf{Step 3: Iterative Reduction}
$$

try it you self https://replit.com/@gewfwewegfwef/CircuitReducer-1
![alt text](image.png)

![alt text](image-1.png)

![alt text](image-2.png)
![alt text](image-3.png)
more examples on parallel circuit
![alt text](image-4.png)
![alt text](image-5.png)