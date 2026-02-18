# Hexapod One-Leg Inverse Kinematics Simulation

This repository contains Python simulations and Inverse Kinematics (IK) solvers for a single leg of a hexapod robot. The project allows for visualizing leg trajectories, calculating joint angles, and verifying movement ranges.

## Project Description

The Hexapod One-Leg Simulation project is a comprehensive toolkit designed to aid in the development and testing of hexapod robot locomotion. It focuses on the mathematical modeling and visualization of a single leg's kinematics, providing a sandbox for validating inverse kinematics algorithms before deploying them to physical hardware.

The core of the repository consists of Python scripts that simulate the 3-degree-of-freedom (3-DOF) leg structure, comprising the Coxa, Femur, and Tibia links. The IK solver (`single_leg_ik_viz.py`) calculates the necessary joint angles to reach a specific target coordinate in 3D space, ensuring the leg moves smoothly and correctly. The extended simulation (`single_leg_ik_extended.py`) offers additional features for verifying reachable workspaces and exporting joint configurations.

A key feature is the trajectory simulation (`leg_trajectory_sim.py`), which generates linear paths and visualizes how the leg follows them. This is crucial for developing gait algorithms, such as the tripod or wave gait, where precise foot placement is essential for stability. The tools output detailed coordinate and angle data to the `output/` directory, which can be used for debugging or interfacing with firmware.

This project serves as a foundational building block for full hexapod control, allowing developers to isolate and perfect the mechanics of individual limbs. It requires `numpy` and `matplotlib` for calculation and 3D visualization.

## File Structure

- **`leg_trajectory_sim.py`**: Simulates the leg following a linear trajectory (e.g., a stride) and visualizes the movement.
- **`single_leg_ik_viz.py`**: Visualizes a single leg's pose for a given target coordinate and exports the resulting joint coordinates.
- **`single_leg_ik_extended.py`**: An extended version composed of more features for testing joint limits and exporting angles.
- **`output/`**: Directory where generated data files (coordinates and poses) are saved.

## Usage

### Prerequisites
- Python 3.x
- NumPy
- Matplotlib

Install dependencies:
```bash
pip install numpy matplotlib
```

### Running the Simulations

1. **Trajectory Simulation**:
   ```bash
   python leg_trajectory_sim.py
   ```
   This will open a 3D plot showing the leg moving along a defined path.

2. **Single Leg IK Visualization**:
   ```bash
   python single_leg_ik_viz.py
   ```
   Calculates IK for a specific target and saves coordinates to `output/one_leg_coordinates.txt`.

3. **Extended Simulation**:
   ```bash
   python single_leg_ik_extended.py
   ```
   Performs IK calculations and exports poses to `output/one_leg_poses_extended.txt`.

## Output Files

The scripts generate `.txt` files in the `output/` folder containing:
- **`one_leg_coordinates.txt`**: Cartesian coordinates of each joint (Hip, Knee, Ankle, Tip).
- **`one_leg_poses_extended.txt`**: Joint angles (Theta Hip, Theta Femur, Theta Tibia) in degrees.
