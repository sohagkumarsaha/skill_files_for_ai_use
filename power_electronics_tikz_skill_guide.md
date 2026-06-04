# Power Electronics TikZ Circuit Drawing Skill Guide

## Objective

This skill file is designed to help an AI system generate **publication-quality IEEE-style TikZ power electronics schematics** from:
- screenshots,
- textbook figures,
- journal images,
- hand-drawn converter diagrams,
- or topology sketches.

The generated circuits must be:
- electrically meaningful,
- geometrically symmetric,
- visually balanced,
- and directly compilable in Overleaf.

---

# Core Engineering Philosophy

The AI must behave like an expert power electronics engineer and NOT like a generic diagram tracer.

The objective is:
1. Understand the converter topology.
2. Reconstruct the electrical meaning.
3. Produce a clean professional schematic.
4. Maintain IEEE publication-quality aesthetics.

---

# Mandatory Engineering Rules

## 1. Preserve Electrical Topology

Always preserve:
- switching-leg structure,
- current paths,
- midpoint nodes,
- passive filter arrangement,
- transformer polarity,
- DC bus structure,
- grounding,
- antiparallel diode orientation,
- modulation/output terminals.

Never distort the electrical meaning for visual convenience.

---

## 2. Symmetry Rules

For bridge converters:
- left and right switching legs must be symmetric,
- midpoint nodes must align horizontally,
- upper and lower devices must be vertically centered,
- output branches must be centered between switching devices.

---

## 3. Preferred TikZ Style

Always use:

```latex
\usepackage[american, cuteinductors, smartlabels]{circuitikz}
```

Preferred style configuration:

```latex
\ctikzset{bipoles/thickness=1}
\ctikzset{bipoles/length=0.85cm}
\ctikzset{bipoles/diode/height=.38}
\ctikzset{bipoles/diode/width=.32}

\tikzstyle{every node}=[font=\small]

\tikzstyle{every path}=[
    line width=0.9pt,
    line cap=round,
    line join=round
]
```

---

# IGBT Drawing Standard

Use enlarged IGBTs:

```latex
\tikzset{
    igbt/.style={
        nigbt,
        scale=1.35
    }
}
```

Preferred style:
- large enough for publication,
- proportional to passive components,
- visually dominant switching elements.

---

# Antiparallel Diode Rules

Each IGBT must include:
- proper antiparallel diode,
- correct orientation,
- balanced spacing,
- compact wiring.

Preferred structure:

```latex
\draw
(Q1.E) ++(0,0.12)
    -- ++(0.42,0)
    to[D*]
    ($(Q1.C)+(0.42,-0.12)$)
    -- ++(-0.42,0);
```

---

# DC Bus Rules

## Correct Practices

- DC rails should terminate shortly after final connection.
- Avoid unnecessarily long rails.
- DC+ and DC− labels should remain compact.

Preferred:

```latex
\draw (VdcTop) -- ++(6.0,0);
\draw (0,0) -- ++(6.0,0);
```

---

# Midpoint Node Rules

For bridge converters:
- midpoint nodes must represent actual electrical outputs,
- output filters must connect to midpoint nodes,
- dots must be centered and aligned.

Preferred:

```latex
\coordinate (Aout) at ($(Q1.E)!0.5!(Q2.C)$);
\filldraw (Aout) circle (1.8pt);
```

---

# Output Branch Rules

## Correct Practice

The output branch:
- must be centered,
- must not overlap annotations,
- must preserve proportional spacing.

Preferred:

```latex
\draw
(Aout)

    to[short]
    ++(0.20,0)

    to[L,l_=$L_f$]
    ++(1.05,0)

    to[R,l_=$R_L$]
    ++(1.15,0)

    -- (Bout);
```

---

# Annotation Rules

## Current Annotation

Current arrows:
- should not overlap components,
- should remain above branch,
- should align with current direction.

Preferred:

```latex
\draw[-latex]
    ($(Aout)+(0.4,0.25)$)
    -- ++(0.8,0);

\node[above]
at ($(Aout)+(0.8,0.20)$)
{$i_o(t)$};
```

---

## Voltage Annotation

Voltage labels:
- should align with measured element,
- polarity should remain readable,
- avoid collision with current arrow.

Preferred:

```latex
\node at ($(Bout)+(-1.55,.18)$) {$+$};
\node at ($(Bout)+(-0.55,0.18)$) {$-$};

\node[above]
at ($(Bout)+(-1,0.00)$)
{$v_o(t)$};
```

---

# Layout Quality Rules

Always ensure:
- no overlapping text,
- no oversized whitespace,
- balanced horizontal spacing,
- balanced vertical spacing,
- proportional component scaling,
- compact professional layout.

---

# Engineering Interpretation Rules

The AI must infer:
- converter type,
- current flow,
- power stage structure,
- filter placement,
- transformer orientation,
- semiconductor arrangement,
- missing driver circuitry.

Do NOT blindly trace pixels.

---

# Supported Converter Families

The skill must support:
- VSI,
- CSI,
- H-bridge,
- full bridge,
- half bridge,
- DAB,
- MMC,
- NPC,
- ANPC,
- buck,
- boost,
- buck-boost,
- Ćuk,
- SEPIC,
- flyback,
- forward converter,
- push-pull,
- resonant converters,
- multilevel inverters,
- matrix converters,
- AC-DC rectifiers,
- active front-end converters,
- battery converters,
- EV charger topologies,
- microgrid converters,
- SST architectures.

---

# Output Requirements

Generated output must:
- compile directly in Overleaf,
- use standalone class,
- avoid unnecessary packages,
- maintain IEEE-quality aesthetics,
- use clean naming conventions,
- preserve original topology.

---

# Sample Prompt Template

## Generic Prompt

```text
Analyze the uploaded power electronics circuit image and recreate it as a publication-quality IEEE-style standalone TikZ schematic.

Requirements:
- Use circuitikz.
- Preserve exact electrical topology.
- Use enlarged IGBTs with antiparallel diodes.
- Keep symmetric converter layout.
- Center midpoint output branches.
- Maintain professional power electronics drawing style.
- Use compact DC rails.
- Ensure clean annotations and spacing.
- Output complete standalone Overleaf-compatible LaTeX code only.
```

---

# Advanced Prompt Template

```text
Analyze the uploaded converter topology image as an expert power electronics engineer.

Do not trace visually only. Infer the actual electrical topology and reconstruct the converter professionally.

Requirements:
- Publication-quality IEEE schematic.
- Symmetric bridge geometry.
- Correct semiconductor orientation.
- Compact wiring.
- Proper midpoint nodes.
- Balanced spacing.
- Clean current and voltage annotations.
- Preserve exact topology from source image.
- Generate standalone TikZ LaTeX code compatible with Overleaf.
- Avoid unnecessary decorative elements.
- Use engineering-quality spacing and alignment.
```

---

# Common Mistakes To Avoid

## Never:
- create asymmetric bridge legs,
- use extremely long DC rails,
- overlap annotations,
- distort passive component spacing,
- connect branches to incorrect node heights,
- place current arrows through components,
- use inconsistent device scaling,
- create floating electrical nodes accidentally,
- leave broken connections,
- add unnecessary graphical decorations.

---

# Final Goal

The final generated schematic should look comparable to:
- IEEE Transactions papers,
- CPSS journal figures,
- high-quality PhD dissertation converter diagrams,
- professional converter topology illustrations used in advanced power electronics literature.
