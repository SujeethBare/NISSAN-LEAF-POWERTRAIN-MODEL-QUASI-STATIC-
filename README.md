# Powertrain Quasi-Static Model

MATLAB/Simulink **quasi-static (backward-facing)** model of an electric vehicle (Nissan Leaf class), used to calculate road loads, motor and battery demand, and energy consumption over different drive cycles. A **rotary switch** in the model lets you choose which drive cycle to run.

---

## Aim

- Model the vehicle's resistive forces and evaluate the motor and battery pack demand across different drive cycles
- Use the results to size powertrain components: gear ratio, motor, battery pack, and current-rated parts such as conductors, contactors and fuses

---

## Approach

### 1. Drive cycles
- Several drive cycles included and selected with a **rotary switch**: Artemis Rural (ARDC), Artemis Urban (AUDC) and a modified NEDC (MNEDC)
- Speed–time profile of the chosen cycle drives the whole model

### 2. Vehicle resistive forces
- **Rolling**, **grade**, **aerodynamic** and **acceleration/inertial** forces calculated at every time step
- Influence of each force on the total tractive demand studied

### 3. Motor and battery pack
- Wheel demand converted to motor torque and speed through the gear ratio
- Motor and controller **efficiency maps** applied for both **motoring** and **regenerative** operation
- Traction battery pack modeled from cell datasheet values (series/parallel configuration) to evaluate:
  - Battery power and current (**peak** and **nominal**)
  - Cell **C-rates**
  - **Energy per km** and total energy for the cycle or required range

---

## Repository guide

| File | What it does |
|---|---|
| `Quasi_Static_Model.m` | Vehicle, motor and battery parameters, and data import |
| `QUASI_STATIC_MODEL_SIM.slx` | Quasi-static Simulink model with the drive cycle selector switch |

**Data files** (keep them in the same folder):

| File | Contents |
|---|---|
| `ARDC.xlsx` | Artemis Rural drive cycle |
| `AUDC.xlsx` | Artemis Urban drive cycle |
| `MNEDC.xlsx` | Modified NEDC drive cycle |
| `Nissan_Leaf_Motor_Efficiency.xls` | Motor efficiency map (motoring) |
| `Nissan_Leaf_Motor_Regenerative_efficiency.xls` | Motor efficiency map (regen) |
| `Nissan-Leaf-Motor-Controller-Efficiency.xlsx` | Motor controller efficiency (motoring) |
| `Nissan-leaf-motor-controller-regenerative-efficiency.xlsx` | Motor controller efficiency (regen) |

---

## How to run

1. Open MATLAB and set the repository folder as the current folder
2. Run `Quasi_Static_Model.m`
3. Open `QUASI_STATIC_MODEL_SIM.slx`, choose a drive cycle with the slider switch, and run the simulation
