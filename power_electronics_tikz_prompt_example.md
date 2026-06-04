Analyze the uploaded screenshot of the power electronics converter and recreate it as a publication-quality IEEE-style standalone TikZ schematic in LaTeX.



The uploaded image is a Dual Active Bridge (DAB) converter topology with:

- two full bridges,

- high-frequency transformer,

- leakage/output inductance,

- DC-link capacitors,

- output capacitor and load,

- antiparallel diodes,

- current and voltage annotations.



Requirements:



1. Use:

\usepackage[american, cuteinductors, smartlabels]{circuitikz}



2. Generate complete standalone Overleaf-compatible LaTeX code.



3. Preserve the exact electrical topology and switching structure from the screenshot.



4. Use enlarged IGBTs/MOSFETs with antiparallel diodes in professional IEEE power electronics style.



5. Maintain:

- symmetric bridge geometry,

- aligned midpoint nodes,

- centered transformer placement,

- compact DC rails,

- balanced spacing,

- proportional component scaling.



6. Reconstruct the topology as an expert power electronics engineer:

- infer true electrical connections,

- preserve current paths,

- preserve transformer polarity and turns ratio notation,

- preserve capacitor and inductor placement,

- preserve node labels (a,b,c,d),

- preserve current labels (ib1, ib2, ip, iL, io),

- preserve voltage labels (vab, vcd, vo).



7. Ensure:

- no overlapping annotations,

- no excessively long wires,

- no floating nodes,

- no asymmetry,

- no distorted transformer geometry.



8. Current arrows and voltage polarity annotations must be:

- clean,

- readable,

- properly aligned,

- electrically meaningful.



9. Use publication-quality spacing comparable to:

- IEEE TPEL,

- IEEE TIE,

- CPSS,

- high-quality PhD dissertation figures.



10. Output ONLY the final LaTeX TikZ code.



Do not provide explanations.

Do not summarize the circuit.

Do not omit any component from the screenshot. 

