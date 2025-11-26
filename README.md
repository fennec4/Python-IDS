# Python-IDS

# Real-Time Hybrid Intrusion Detection System (IDS)

## Project Overview

This repository contains the code for a **Real-Time Intrusion Detection System (IDS)** built using Python 3 and open-source libraries. An IDS functions like a **security camera for your network**, monitoring traffic to detect potential cyber attacks and security breaches.

This project implements a **hybrid IDS**, combining two primary detection methods to monitor network traffic:

1.  **Signature-based Detection:** Identifies known attack patterns using predefined rules (e.g., detecting SYN floods or port scans).
2.  **Anomaly-based Detection:** Identifies unusual behavior using heuristics and machine learning [2]. This system uses the **Isolation Forest** model from `scikit-learn` to differentiate typical traffic patterns from anomalies.

The system is structured as a **Network-based IDS (NIDS)** and operates as a proof-of-concept for understanding core network security fundamentals.

## Core Components

The IDS is modular, consisting of four main components:

1.  **Packet Capture Engine:** Uses **Scapy** to capture network packets in real time from a specified interface (e.g., `eth0`).
2.  **Traffic Analysis Module:** Processes captured packets, tracking connection flows and extracting features like packet rate, flow duration, and TCP flags.
3.  **Detection Engine:** Implements the hybrid detection mechanisms (signature and anomaly) to identify threats and assign a confidence score.
4.  **Alert System:** Uses Python's `logging` module to process detected threats and log them in a structured JSON format (defaulting to `ids_alerts.log`). High-confidence threats (confidence > 0.8) are escalated as `CRITICAL` alerts.

## Prerequisites and Installation

To run this IDS, you must have Python 3 installed. The following open-source libraries must be installed using `pip`:

```bash
pip install scapy python-nmap numpy sklearn
```
Usage and Execution
Running the IDS
The IDS must be run with root or administrative privileges because packet capture requires low-level network access.
1. Save the code as ids.py.
2. Identify your active network interface (e.g., eth0, wlan0) using ifconfig. If your interface is not eth0, you must specify it when running the script (e.g., IntrusionDetectionSystem(interface="wlan0")).
3. Execute the script using sudo:
sudo python3 ids.py
The system will print Starting IDS on interface [interface name] and run continuously until manually stopped (e.g., by pressing Ctrl+C).
Testing Functionality
You can test the system's detection logic against simulated network traffic, including SYN flood and port scan simulations, by calling the test_ids() function within the main execution block.
Source and Attribution
This project is based on the tutorial:
"How to Build a Real-Time Intrusion Detection System with Python and Open-Source Libraries"
• Source: [Excerpts from the article provided.](https://www.freecodecamp.org/news/build-a-real-time-intrusion-detection-system-with-python/)
