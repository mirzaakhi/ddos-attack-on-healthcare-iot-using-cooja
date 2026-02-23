# DDoS Attack on Healthcare-IoT Devices using Cooja Simulator

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
- Node 1 → Server (built-in `rpl-udp` example in Cooja)  
- Nodes 2–16 → Normal sensor nodes  
- Nodes 17–20 → DDoS attack nodes  

---

## ⏱ Traffic Logic

- Normal nodes send data every **60 seconds**
- DDoS nodes send data every **30 seconds**

This means:

- Normal node → 1 packet per minute  
- DDoS node → 2 packets per minute  

The attack is modeled as higher-frequency UDP traffic.

---

## 🛠 Requirements

- Contiki OS
- Cooja simulator
- Sky mote target

---

## ▶️ How to Run the Simulation

1. Clone the repository and navigate into the project folder:
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
2. Run Cooja.  
   (Installation guide:  
   https://medium.com/@mirzaakhi/how-to-install-contikios-and-run-cooja-simulator-on-windows-11-with-oracle-vm-virtualbox-2691fce267af)

3. Add the server mote:
   - Click Motes
   - Add skymotes
   - Choose **Compile from source**
   - Browse to the following directory inside Contiki:
      `contiki/examples/rpl-udp`
   - Select `udp-server.c` and open it
   - Click on Compile and then click on Create
   - In the Create Motes window, set Number of new motes to 1
   - Click on Add motes

4. Add normal Healthcare IoT sensor motes:
   - Click Motes
   - Add skymotes
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 15

5. Add DDoS attack motes:
   - Click Motes
   - Add skymotes
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 4

6. Start the simulation.

---

## 📊 Log File

After running the simulation, save the output log as:

`iotddoslog.txt`
