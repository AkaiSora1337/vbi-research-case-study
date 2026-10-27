# Methodology

## 1. Define the modeling boundary

The first task was to distinguish three kinds of information:

- quantities directly supported by engineering references;
- equivalent assumptions needed to build a computational model;
- calibration choices introduced to reproduce selected reference behavior.

Keeping these categories separate reduces the risk of presenting an equivalent model as an as-built structural representation.

## 2. Build traceable model checks

The verification workflow included checks at several levels:

| Level | Example questions |
|---|---|
| Geometry | Are spans, deck extent, supports, and contact coordinates mutually consistent? |
| Mass | Is total mass preserved? Is its spatial distribution intentional? |
| Matrices | Are mass and stiffness matrices symmetric and numerically well-conditioned for the intended solve? |
| Interfaces | Does the contact mapping preserve force, motion compatibility, and virtual work? |
| Dynamics | Are modal pairings meaningful, rather than selected only because frequencies are close? |
| Integration | Do smaller time steps materially change the reported quantities? |
| Spatial resolution | Do refined meshes change the controlling response or its location? |

## 3. Test response sensitivity

Peak displacement and peak acceleration were treated separately. Global displacement can appear converged even when a local acceleration peak remains sensitive to contact smoothing, bridge-end geometry, or time step.

A result was therefore reported together with:

- the quantity and spatial scope being measured;
- the time step and mesh used;
- the comparison case;
- the relative change;
- the limitations of that comparison.

## 4. Control long-running simulations

Long traffic simulations require operational checks in addition to equations. The workflow tracked:

- declared inputs and hashes or equivalent provenance records;
- solver completion and finalization status;
- iteration counts and convergence tolerances;
- non-finite values and incomplete output;
- vehicle entry and exit coverage;
- memory and storage boundaries;
- which response fields were retained and which could not be reconstructed later.

## 5. Separate conclusion levels

The final review used three practical labels:

- **Diagnostic:** useful for debugging or sensitivity analysis, but not an accepted baseline.
- **Numerically accepted:** passes declared computational checks for a specified case and output scope.
- **Physically validated:** supported by appropriate independent physical or experimental evidence.

The work described here reached different levels for different quantities. It did not treat these labels as interchangeable.

