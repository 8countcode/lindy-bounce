# Bounce Load Lab

An interactive, illustrative biomechanics visualizer for the **lindy-hop bounce** — the rhythmic, squat-like pulse swing dancers ride on every beat. It shows where the bounce sends its load across the legs (joints vs. muscles) through *every* phase of the movement, to help find a posture that protects the knees, hips, and lower back over years of dancing.

**Live demo:** https://8countcode.github.io/lindy-bounce/

## What it does

- **Easy mode by default (한국어 / English):** opens on a beginner-friendly, mobile-first view with a swipeable carousel of example bounces — a *Good vs Bad* side-by-side comparison, curated single examples (gentle pulse, deep squat, …), and a *Custom* bounce you can drag and optimise. Auto-detects browser language with an EN/한 toggle. The full slider/toggle controls live behind **Advanced controls**.
- **Adjustable body proportions:** drag the handle alongside any segment (torso, thigh, shank, foot) to change its length. Changing the body re-derives the curated examples — press **Optimize examples to new body** to search the safest *Good* technique for your proportions and a matched *Bad* contrast. A legend in the figure labels the centre-of-mass, ground-reaction and base-of-support markers.
- **2D sagittal figure** with a bendy foot, posable joints (drag the knee / hip / head), and a heatmap of load across joints and muscles.
- **Four load views:** joint reaction force (×BW), joint moment (N·m), muscle eccentric energy (J), and a generic load %.
- **Dynamics:** a real bounce trajectory with an impact spike at the bottom reversal, a light flight phase when the bounce is energetic, soft-vs-stiff landing, tempo, and single-leg weight share.
- **Balance:** the centre of pressure is computed under the centre of mass; the model flags *tipping forward/backward* and *joint overload* (demand exceeding safe muscle capacity) as two distinct injury channels.
- **Step patterns:** bounce in place, L↔R weight shift, or a triple-step (1 a 2).
- **Top / Bottom poses + path optimiser:** set the two ends of the bounce, then find the path between them that minimises peak load / cumulative load / is smoothest / stays most balanced.
- **A/B comparison:** save two bounces and compare their peak per-joint moments and forces with grouped bar charts.

## Running it

It's a single self-contained `index.html` — no build step, no dependencies. Open it in a browser, or serve the folder:

```sh
python -m http.server 8000
# then open http://localhost:8000
```

## The model (and its limits)

This is an **illustrative** model, not a clinical or lab-grade simulation:

- Quasi-static **centre-of-mass inverse dynamics** in the sagittal plane: each joint's net muscle moment is the torque the body's mass exerts about it (ground reaction under the CoM, minus the gravity of the segments below the joint). Body-segment parameters are textbook (Winter / de Leva).
- Dynamic impact, soft/stiff landing, single-leg scaling, and balance (an extrapolated centre of mass) are grounded in landing-biomechanics literature but applied phenomenologically.
- It is **sagittal-only**, so frontal-plane knee valgus / ACL mechanics are not modelled.

> **Not medical advice.** Forces, moments, and thresholds are order-of-magnitude estimates from population-average literature — not clinical measurements or injury cutoffs. Treat the flags as caution / learning tiers, not pass/fail verdicts. See a qualified physical therapist, physician, or sports-medicine professional for any pain, injury, or personal risk assessment.

## License

Free to use and adapt.
