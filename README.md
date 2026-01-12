# Traffic Light Optimization using Reinforcement Learning

## Overview
This project applies Reinforcement Learning (RL), specifically a Deep Q-Network (DQN), to optimize traffic light phases within a SUMO (Simulation of Urban MObility) environment. The goal is to improve traffic flow efficiency by maximizing average vehicle speed and minimizing waiting times, queue lengths, and lane occupancy.

## Project Structure
The project is organized as follows:

- **`Traffic_Light_Optimization/`**: Root directory of the project.
    - **`traffic_final.ipynb`**: The main Jupyter Notebook containing the implementation of the DQN agent, training loop, and simulation logic.
    - **`Requirements.txt`**: List of dependencies and manual instructions.
    - **`SUMO Files/`**: Contains the SUMO network configurations details (`.net.xml`, `.rou.xml`, etc.) and the main configuration file (`osm.sumocfg`).
    - **`Models/`**: Directory where trained RL models are saved.
    - **`Results/`**: Directory for storing simulation results and metrics.
    - **`Traffic_Simulator (EDA Results and Analysis)/`**: Exploratory Data Analysis files.

## Prerequisites

### 1. Python Libraries
Install the required Python packages using pip:

```bash
pip install numpy matplotlib torch traci
```

### 2. SUMO (Simulation of Urban MObility)
This project requires SUMO to be installed on your system.
- **Download**: [https://eclipse.dev/sumo/](https://eclipse.dev/sumo/)
- **System Path**: Ensure that the `sumo` binary is in your system's PATH so it can be called from the command line.

## Usage

1.  **Navigate to the project directory:**
    ```bash
    cd Traffic_Light_Optimization
    ```

2.  **Configuration Check:**
    - Ensure the `osm.sumocfg` file is properly located in the `SUMO Files` directory or as referenced in the notebook.
    - *Note:* The code expects the configuration file path to be correct. You might need to adjust the `CONFIG_FILE` variable in `traffic_final.ipynb` if your path differs from the hardcoded one (currently like `C:/Users/...`).

3.  **Run the Notebook:**
    Open `traffic_final.ipynb` in Jupyter Notebook or JupyterLab and execute the cells sequentially.
    ```bash
    jupyter notebook traffic_final.ipynb
    ```

## Methodology

### Deep Q-Network (DQN) Agent
The project creates a DQN agent that learns to interact with the traffic environment.
- **State Space**: Includes vehicle counts, queue lengths, mean speeds, waiting times, and occupancy for controlled lanes.
- **Action Space**: Discrete actions representing different traffic light phases and durations.
- **Reward Function**: A weighted combination of:
    - (+) Normalized Average Speed
    - (-) Normalized Average Accumulated Waiting Time
    - (-) Normalized queue Service Time
    - (-) Normalized Lane Occupancy

### Simulation
The simulation runs iteratively, where the agent gathers experience (State, Action, Reward, Next State) to train the neural network, gradually improving its traffic control policy.

## Author
**Hrishikesh Lal Baishya**
