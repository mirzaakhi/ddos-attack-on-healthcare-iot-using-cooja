# DDoS Attack on Healthcare-IoT Devices using Cooja Simulator

This project simulates a Distributed Denial-of-Service (DDoS) attack in a Healthcare Wireless Body Area Network (WBAN) using the Cooja simulator on Contiki OS.

The simulation is based on time interval differences between normal nodes and attack nodes.

---

## 📁 Repository Structure

ddos-attack-healthcare-iot-cooja/
│
├── wban-udp-ddos.c
├── Makefile
├── iotddoslog.txt
└── README.md

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

1. Copy this project folder into the `contiki/examples/` directory.

2. Run Cooja.  
   (Installation guide:  
   https://medium.com/@mirzaakhi/how-to-install-contikios-and-run-cooja-simulator-on-windows-11-with-oracle-vm-virtualbox-2691fce267af)

3. Add the server mote:
   - Click Motes
   - Add skymotes
   - Choose **Compile from source**
   - Select the built-in `rpl-udp` example
   - Set mote count to 1

4. Add normal sensor motes:
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 15

5. Add DDoS attack motes:
   - Click **Browse**
   - Select `wban-udp-ddos.c`
   - Set mote count to 4

6. Start the simulation.

---

## 📊 Log File

After running the simulation, save the output log as:

`iotddoslog.txt`
