# SOFA Soft-Robot Model Predictive Control

Research experiments for simulating and controlling a cable-actuated soft robot in the [SOFA framework](https://www.sofa-framework.org/). The repository progresses from small SOFA examples to Wakrabot simulation, data collection, Koopman-based prediction, and model predictive control.

## Outcomes

- Built SOFA scenes for deformable-body and cable-actuation experiments.
- Collected simulated trajectories and control inputs from a Wakrabot model.
- Constructed lifted linear predictors from simulation data using Koopman-style observables.
- Applied a quadratic-programming MPC controller to cable-force trajectory tracking.

## Repository Map

| Area | Location | Contents |
| --- | --- | --- |
| SOFA tutorials | `Tut1/` | Early scenes, cable controllers, geometry, and position-access experiments. |
| Wakrabot simulation | `Wakrabot/*_wakrabot_cables.py` | SOFA scene definitions for simulation-data collection and closed-loop control. |
| Controllers | `Wakrabot/*_controller.py` | SOFA event controllers and MPC integration. |
| MPC implementation | `Wakrabot/mpc_func.py` | Lifted-state linear MPC and quadratic-program construction. |
| Identification data | `Wakrabot/data_files/` | Simulation trajectories, learned matrices, predictor artifacts, and preparation scripts. |
| Geometry | `Tut1/mesh/`, `Wakrabot/mesh/` | Mesh and CAD assets used by the scenes. |

## Environment

The full simulations require a SOFA installation with SofaPython3 and the plugins referenced by each scene. The numerical scripts additionally use:

- Python 3
- NumPy
- Matplotlib
- qpsolvers with the `quadprog` backend

SOFA plugins and Python bindings are normally installed through a compatible SOFA distribution rather than from PyPI alone.

## Running The Experiments

Run scene files from a SOFA environment so local controller and mesh paths resolve correctly. Representative entry points are:

```text
Tut1/wakrabot_cables.py
Wakrabot/simulation_data_wakrabot_cables.py
Wakrabot/control_wakrabot_cables.py
```

For the numerical MPC experiment without launching a SOFA GUI, use `Wakrabot/mpc_simple_test.py` after installing its Python dependencies.

## Reproducibility Notes

This repository preserves an exploratory research snapshot rather than a packaged application. Paths, SOFA plugin names, and solver availability may need adjustment for a current installation. Files under `data_files/` are retained as experiment inputs and outputs; regenerate them before drawing new quantitative conclusions.

## Portfolio Metadata

`.explorer/project.yml` connects this repository to the generated expedition catalog and the `robotics-and-autonomy` family.