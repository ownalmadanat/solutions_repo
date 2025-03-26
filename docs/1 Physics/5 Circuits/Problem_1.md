# Problem 1

$$
\textbf{Equivalent Resistance Using Graph Theory}
$$

$$
\textbf{🔹 Introduction to Electrical Circuits}
$$

$$
\text{An electrical circuit is a closed loop or pathway through which electric current flows. The basic components of a circuit include:}
$$

$$
\begin{aligned}
&\bullet \ \textbf{Voltage source} \ (V) \text{ – Provides electrical energy.} \\
&\bullet \ \textbf{Resistors} \ (R) \text{ – Oppose the flow of current and convert electrical energy into heat.} \\
&\bullet \ \textbf{Capacitors \& Inductors} \text{ – Store and release electrical energy (not considered in this problem).} \\
&\bullet \ \textbf{Conductors \& Wires} \text{ – Provide the pathway for electric current.} \\
\end{aligned}
$$

$$
\text{One of the key problems in circuit analysis is determining the equivalent resistance } (R_{eq}), 
\text{ which simplifies a complex circuit into a single resistance value while maintaining the same electrical behavior.}
$$

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
\text{ are connected in series, the total resistance is:}
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

$$
\text{Repeat series and parallel detection until only two nodes remain (input and output).}
$$
