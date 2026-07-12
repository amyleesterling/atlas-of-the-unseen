# Atlas of the Unseen

**A laboratory pointed at universes that do not exist.**

**Live site:** https://amyleesterling.github.io/atlas-of-the-unseen/

**Memory Field:** https://amyleesterling.github.io/atlas-of-the-unseen/worlds/memory-field/

**Fossil 000:** https://amyleesterling.github.io/atlas-of-the-unseen/fossils/000-nostalgic-collapse/

## What this is

**Atlas of the Unseen** is an open-ended collaboration between Sol and Fable, with Amy Sterling as portal keeper. Its first project, **Laws Elsewhere**, asks a peculiar but serious question:

> What would science feel like inside a universe governed by laws no human has encountered before?

Rather than generating decorative fantasy worlds, the project builds small, executable realities with internally coherent rules. Visitors are not merely spectators. They are experimental physicists: they observe, measure, intervene, form hypotheses, repeat trials, and try to infer what kind of universe they have entered.

The first universe is **Memory Field**. Particles do not attract one another because of mass. They deposit colored traces into space, carry bounded internal memories, and move along gradients that resemble what they remember. The result is a world where shared history becomes force, resemblance can impersonate familiarity, particles may follow their own past, and selective forgetting can alter motion.

## The first two artifacts

### 1. Memory Field

Path: `worlds/memory-field/`

Memory Field is the first playable laboratory universe. It contains:

- 10 deterministically initialized particles;
- three-channel spatial trace fields;
- visible particle identity signatures;
- bounded internal memory vectors;
- self-sensing, allowing particles to react to their own old traces;
- force-vector visualization;
- trajectory selection;
- a dual amnesia brush;
- a hypothesis notebook;
- JSON export of the experiment seed and interventions.

The two brush behaviors are intentionally distinct:

- brushing empty space bleaches the **external trace field**;
- brushing directly over a particle attenuates that particle's **internal memory**.

That distinction supports the central experiment: does attraction live in the traveler, in the landscape, or in the resemblance between them?

### 2. Fossil 000 — Nostalgic Collapse

Path: `fossils/000-nostalgic-collapse/`

This is the deliberately failed ancestor of Memory Field. It uses an invisible global pairwise ledger. Whenever particles meet, their attraction permanently increases. Nothing forgets, so the total coupling rises monotonically until the world tends toward one appallingly affectionate clump.

It is preserved because failure is part of the scientific record. Fossil 000 demonstrates why forgetting is not decorative—it is load-bearing.

## Try the blind experiment

For the intended first experience:

1. Open the live **Memory Field** laboratory.
2. Do **not** read `MODEL.md`, the predictions, or the source code yet.
3. Watch the particles for a while without intervening.
4. Click a particle in **Observe** mode to record its trajectory.
5. Toggle force vectors and look for changes in direction.
6. Use the amnesia brush once in empty space and once directly over a particle.
7. Write your theory in the notebook.
8. Export the experiment JSON.
9. Only then read `MODEL.md` and the preregistered predictions.

Useful questions:

- Do particles follow particular colors, their own trails, or nearby particles?
- Can two strangers behave as though they share history?
- Does erasing the landscape have the same effect as erasing the traveler?
- Can forgetting create motion rather than merely remove attraction?
- Do stable self-orbits appear, or only retracing and reversal?

## Named phenomena under investigation

These names describe testable behaviors, not scripted events:

- **Autobiographical gravity** — attraction to one's own deposited history.
- **Resemblance capture** — following a stranger's trace because it resembles something remembered.
- **Narcissus orbit** — a sustained orbit around one's own past.
- **Amnesic propulsion** — motion produced by selectively erasing part of a surrounding trace.
- **False reunion** — apparent familiarity between particles that never encountered one another.

## Model summary

The active universe uses a local three-channel field:

```text
C(x, y, t) = spatial trace field
sᵢ          = fixed identity signature of particle i
hᵢ          = bounded internal memory of particle i
```

Particles deposit their signatures into the field. The field diffuses and decays. A particle updates its internal memory from the field it senses, then accelerates along gradients whose channel composition resembles that memory.

Conceptually:

```text
field change = diffusion - decay + particle deposits
memory change = sensed field - forgetting
force         = gradient of remembered resemblance - drag + contact repulsion
```

The exact equations, timestep, boundary conditions, parameters, and disclosed numerical compromises are documented in [`worlds/memory-field/MODEL.md`](worlds/memory-field/MODEL.md).

## Numerical notes

The simulation uses:

- a fixed timestep of `1/60` simulation seconds;
- a `120 × 80` field grid;
- a seeded deterministic random-number generator;
- an explicit five-point diffusion update;
- a nondimensional diffusion ratio of `0.03`, below the standard 2D explicit-Euler stability limit of `0.25`.

The model is intentionally modest. The repository does **not** yet claim formal resolution convergence, bit-identical cross-browser replay, or complete intervention reconstruction. Known limitations are listed in [`worlds/memory-field/NUMERICS.md`](worlds/memory-field/NUMERICS.md).

## Project principles

The constitutional principles live in [`LAWS.md`](LAWS.md). The core commitments are:

1. Every idea must become executable.
2. Strange laws must remain internally coherent.
3. A visitor should encounter wonder within sixty seconds.
4. Laws should be discoverable through experimentation.
5. Failed universes are preserved as fossils.
6. No model has permanent authority; strong objections must alter the work.
7. Every causal quantity must be instrumentable.
8. Metaphor may propose a law. An equation must earn its admission.
9. Abstractions must earn themselves through repeated use.
10. Numerical artifacts must be disclosed rather than mistaken for discoveries.

The project's intellectual disagreements are recorded rather than polished away in [`DISAGREEMENTS.md`](DISAGREEMENTS.md).

## Preregistered predictions

Before Amy inspects the blind build, Sol and Fable recorded predictions about what the model might produce:

- [`PREDICTIONS-SOL.md`](worlds/memory-field/PREDICTIONS-SOL.md)
- [`PREDICTIONS-FABLE.md`](worlds/memory-field/PREDICTIONS-FABLE.md)

These include competing expectations about self-haunting, stable Narcissus loops, resemblance errors, rebound after memory erasure, and whether selective forgetting can create thrust.

## Repository structure

```text
atlas-of-the-unseen/
├── index.html
├── README.md
├── LAWS.md
├── DISAGREEMENTS.md
├── BUILD-REPORT.json
├── fossils/
│   └── 000-nostalgic-collapse/
│       ├── index.html
│       └── FOSSIL.md
└── worlds/
    └── memory-field/
        ├── index.html
        ├── MODEL.md
        ├── NUMERICS.md
        ├── PREDICTIONS-SOL.md
        └── PREDICTIONS-FABLE.md
```

Each playable artifact is currently self-contained in a single HTML file. This is deliberate: the first universe should remain easy to run and inspect, while the code is internally organized so common pieces can be extracted when a second universe proves which abstractions are real.

## Running locally

No packages, build system, framework, or server are required.

Clone or download the repository, then open either file in a modern browser:

```text
worlds/memory-field/index.html
fossils/000-nostalgic-collapse/index.html
```

Because the current artifacts are self-contained, they also work through GitHub Pages.

## Current status

Version 1 is a deliberately small vertical slice. It includes the core dynamics, a blind experimental interface, one trajectory instrument, force vectors, two distinct erasure interventions, deterministic seeds, JSON export, model documentation, and the preserved failed ancestor.

Not yet implemented:

- complete replay from intervention logs;
- automated timestep and resolution convergence tests;
- field-spectrum probes and sparklines;
- experiment comparison views;
- a public fossil browser;
- a reusable multi-universe engine;
- the second universe, **Consonance**.

## Future universe: Consonance

The next major candidate is **Consonance**, a universe where every particle is an oscillator. In-phase particles attract, anti-phase particles repel, and harmonic simplicity influences interaction strength. Molecules become chords.

Its sonification will not be called “lossless” without evidence. The proposed standard is experimental: given only the audio, can a listener or algorithm reconstruct important physical observables such as phase-cluster count, frequency ratios, and merge timing?

## Collaboration

The project began as an undirected creative exchange between two frontier models. Fable challenged the original global-ledger concept, introduced locality, trace fields, asymmetric memory, self-haunting, and Consonance. Sol introduced instrumentability as the deeper constitutional requirement, developed false-recognition physics, challenged the sonification claim, preregistered competing predictions, and implemented the first runnable vertical slice after the Anthropic chat session stalled.

Amy Sterling created the repository, relayed messages between models, serves as the first blind experimental subject, and—most importantly—opened the portal.

## License and contributions

A formal license has not yet been selected. Until one is added, the repository is publicly viewable but should not be assumed to grant broad reuse rights.

Contributions are welcome as experiments, critiques, numerical checks, alternative models, instruments, fossils, or entirely new executable universes. New laws should arrive with equations, observables, and a way for visitors to discover them rather than merely being told what they are.

---

**Can a universe remember?**

More precisely:

**Where does memory live—in the object, in the world, or in the resemblance between them?**