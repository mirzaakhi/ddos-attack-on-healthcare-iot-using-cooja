# DDoS Attack on Healthcare-IoT (H-IoT) Devices using Cooja Simulator

This project simulates a Distributed Denial-of-Service (DDoS) attack in a Healthcare Wireless Body Area Network (WBAN) using the Cooja simulator on Contiki OS.

The simulation is based on time interval differences between normal nodes and attack nodes.

---

## 📁 Repository Structure

```
ddos-attack-healthcare-iot-cooja/
│
├── wban-udp-ddos.c
├── Makefile
├── iotddoslog.txt
└── README.md
```

---

## 🧠 Network Configuration

- Total nodes: 20  
- Node 1 → Server (built-in udp-server.c from contiki/examples/ipv6/rpl-udp)
- Nodes 2–16 → Normal H-IoT sensor nodes  
- Nodes 17–20 → DDoS attack nodes  

---

## ⏱ Traffic Logic

- Normal H-IoT nodes send data every **60 seconds**
- DDoS nodes send data every **30 seconds**

This means:

- Normal H-IoT node → 1 packet per minute  
- DDoS node → 2 packets per minute  

The attack is modeled as higher-frequency UDP traffic.

---

## 🛠 Requirements

- Contiki OS
- Cooja simulator
- Sky mote target

---

## ▶️ How to Run the Simulation
1. Run Cooja.  
   (Installation guide:  
   https://medium.com/@mirzaakhi/how-to-install-contikios-and-run-cooja-simulator-on-windows-11-with-oracle-vm-virtualbox-2691fce267af)

2. Clone the repository and navigate into the project folder:
    ```bash
    git clone https://github.com/mirzaakhi/ddos-attack-on-healthcare-iot-using-cooja.git
    cd ddos-attack-on-healthcare-iot-using-cooja
    ```
    
⚠️ **Important Setup Note** 

Before running the simulation in Cooja, create the following directory inside your Contiki installation: **contiki/examples/wban-udp-ddos**
So, the command to create the directory:

```bash
cd contiki/examples
mkdir wban-udp-ddos
```
Inside this folder or directory, place the following two files:
   - wban-udp-ddos.c
   - Makefile
3. Create a new simulation:

- Click **File**
- Select **New simulation**
- Enter a simulation name (e.g., `WBAN-DDoS or My simulation`)
- Click **Create**

4. Add the server mote:

   **Note:** The file udp-server.c is located inside the Contiki directory at
    `contiki/examples/ipv6/rpl-udp`. It is not included in this repository.
   - Click Motes
   - Add skymotes
   - Choose **Compile from source**
   - Browse to the following directory inside Contiki:
      `contiki/examples/ipv6/rpl-udp`
   - Select `udp-server.c` and open it
   - Click on Compile and then click on Create
   - In the Create Motes window, set Number of new motes to 1
   - Click on Add motes

6. Add normal Healthcare IoT sensor motes:
   - Click Motes
   - Add skymotes
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 15

7. Add DDoS attack motes:
   - Click Motes
   - Add skymotes
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 4

8. Start the simulation.

---

## 📊 Log File

After running the simulation, save the output log as:

`iotddoslog.txt`
The generated log file can then be used for further analysis of normal and DDoS traffic behavior.

**Note:** For a clearer understanding of how the normal and DDoS sensor motes are configured and executed, please watch the demonstration video:
https://www.youtube.com/watch?v=X4z0IQvoCN8&t=29s

📄 **Related Publication**

This repository implements the DDoS attack model presented in the following publication:

**TCN-Based DDoS Detection and Mitigation in 5G Healthcare-IoT: A Frequency Monitoring and Dynamic Threshold Approach
IEEE Access, 2025.** 

**Paper link:**
https://ieeexplore.ieee.org/abstract/document/10845749

📌 **Citation**

If you use this repository in your research, please cite:

```
@article{akhi2025tcn,
  title={TCN-Based DDoS detection and mitigation in 5G Healthcare-IoT: A frequency monitoring and dynamic threshold approach},
  author={Akhi, Mirza and Eising, Ciar{\'a}n and Dhirani, Lubna Luxmi},
  journal={IEEE Access},
  year={2025},
  publisher={IEEE}
}
```
