# Chiron

**Computational physics, in the browser.**

Three classic simulations from my undergraduate computational-physics coursework
(PH30056, ~2011), originally written in C with OpenGL/GLUT — rebuilt as interactive,
self-contained web apps. No build step, no dependencies, no server: every simulation
runs entirely in the browser.

🔗 **[Live site](https://mikebertin.github.io/chiron/)**

## The simulations

| | | |
|---|---|---|
| **[Diffusion-Limited Aggregation](dla/)** | Fractal growth | Random walkers stick into a branching fractal; fractal dimension (~1.71) computed live. Sticking probability, seed shapes, and 4-/8-neighbour sticking are adjustable. |
| **[The Ising Model](ising/)** | Phase transition | A Metropolis Monte Carlo lattice of spins. Cross the critical temperature (T꜀ ≈ 2.269) to watch magnetic order appear and dissolve. Auto-sweep traces the magnetisation curve. |
| **[Molecular Dynamics](md/)** | Melting & freezing | Lennard-Jones atoms integrated with the Verlet algorithm. Heat the crystal until it melts, cool the liquid until it re-freezes; atoms coloured by speed. |

## Notes on the port

The physics is faithful to the original coursework, with a few modernisations for the web:

- **DLA** implements the textbook radial walk (birth circle, jump optimisation, sticking
  probability) that the original's circle-spawn code intended.
- **Ising** is the same Metropolis update with a periodic lattice and an energy/probability
  lookup table; the temperature sweep that the original wrote to disk is now a live plot.
- **MD** uses a fully periodic box (the original was periodic in x only) and a
  velocity-rescaling thermostat with velocity Verlet, in place of the original's
  precomputed initial-conditions file.

Named for [Chiron](https://en.wikipedia.org/wiki/Chiron), the centaur who tutored the
heroes of Greek myth.

## Running locally

It's all static files — open `index.html`, or serve the folder:

```sh
python3 -m http.server 8730
```

Then visit <http://localhost:8730>.
