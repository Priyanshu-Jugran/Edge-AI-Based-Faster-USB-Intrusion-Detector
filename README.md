# Edge AI Based Faster USB Intrusion Detection & Protection System

## Overview

The Edge AI Based Faster USB Intrusion Detection & Protection System is a cybersecurity project developed to detect and prevent USB-borne malware using Machine Learning and Edge AI.

USB devices remain one of the most common attack vectors for malware propagation, especially in offline environments where traditional cloud-based security solutions may not be available. This project provides a lightweight and intelligent solution that performs malware detection locally on the endpoint device.

The system combines:

* Signature-Based Scanning
* Behavior-Based Scanning
* Edge AI Inference using ONNX Runtime
* Real-Time USB Detection
* Automatic USB Isolation
* Graphical User Interface (GUI)

All predictions are performed locally without requiring internet connectivity.

---

## Problem Statement

USB storage devices are widely used for data transfer and frequently become a medium for spreading malware, ransomware, trojans, and malicious scripts.

Traditional antivirus solutions often depend on:

* Internet connectivity
* Signature database updates
* Cloud processing

This project aims to provide an offline and intelligent USB security solution capable of detecting both known and suspicious threats before they can affect the host system.

---

## Key Features

* Real-time USB insertion detection
* Signature-based malware detection
* Behavior-based threat detection
* Edge AI powered inference
* ONNX Runtime integration
* Hybrid scanning architecture
* Automatic USB isolation and unmounting
* Parallel scanning using multithreading
* Offline operation
* User-friendly Tkinter GUI
* Lightweight and fast execution

---

## Technologies Used

### Programming Language

* Python

### Libraries

* os
* time
* math
* psutil
* threading
* pandas
* numpy
* tkinter
* onnxruntime

### Machine Learning

* Random Forest Classifier
* ONNX
* ONNX Runtime

---

## Project Evolution

The repository contains all development phases of the project.

### Phase 1 – Dataset Preparation

Created and prepared a signature-based malware dataset containing:

* Safe files
* Executable files
* Script files
* Potentially suspicious files

Features extracted:

* File Size
* Extension Flag
* Entropy

Folder:

```text
01_SignatureDataset
```

---

### Phase 2 – Model Training & Selection

Multiple machine learning algorithms were trained and evaluated.

Algorithms explored:

* Logistic Regression
* Decision Tree
* Random Forest
* Support Vector Classifier

Best performing model was selected and saved.

Folder:

```text
02_SignatureModel
```

---

### Phase 3 – Signature Scanner (Without GUI)

Implemented:

* USB detection
* Feature extraction
* Malware prediction

Folder:

```text
03_SignProjNoGUI
```

---

### Phase 4 – Signature Scanner with GUI

Added:

* Tkinter interface
* User interaction
* Scan result visualization

Folder:

```text
04_SignatureProject
```

---

### Phase 5 – Edge AI Integration

Migrated model from Joblib format to ONNX.

Benefits:

* Faster inference
* Lower memory consumption
* Edge deployment support

Folder:

```text
05_addingONNXruntime
```

---

### Phase 6 – Behavior-Based Detection

Developed a second AI model for behavior analysis.

Behavior features:

* Read Bytes
* Write Bytes
* File Open Count
* Executable Run Attempts
* Command Process Count

Folder:

```text
06_behaviorModel
```

---

### Phase 7 – Hybrid Detection System

Combined:

* Signature-Based Detection
* Behavior-Based Detection

into a single workflow.

Folder:

```text
07_hybridScanning
```

---

## Final System Workflow

### Step 1: USB Detection

The system continuously monitors removable drives using psutil.

When a new USB device is inserted:

```text
USB Inserted
      ↓
Device Detected
      ↓
Scan Button Activated
```

---

### Step 2: Feature Extraction

Every file present on the USB is analyzed.

Extracted features:

* File Size
* Extension Flag
* Entropy

Entropy is calculated using Shannon Entropy Formula to identify potentially packed or obfuscated files.

---

### Step 3: Signature-Based Scanning

The extracted features are converted into a structured dataset.

Features:

```text
filesize
extflag
entropy
```

The dataset is passed to:

```text
bestAIModel.onnx
```

Prediction:

```text
0 = Safe
1 = Malicious
```

---

### Step 4: Behavior-Based Scanning

Runs simultaneously in a separate thread.

Behavior monitoring collects:

```text
read_bytes
write_bytes
file_open_count
exe_run_attempts
cmd_proc_count
```

These features are passed to:

```text
behavModel.onnx
```

for behavioral threat analysis.

---

### Step 5: Hybrid Decision

Both models contribute to the final decision.

```text
Signature Model
        +
Behavior Model
        ↓
Final Decision
```

This enables detection of:

* Known malware patterns
* Suspicious runtime behavior

---

### Step 6: USB Isolation

After scanning:

```text
mountvol
```

is used to unmount the USB device.

Purpose:

* Prevent malware execution
* Prevent autorun attacks
* Isolate potential threats

---

### Step 7: User Notification

The GUI displays:

For malicious USB:

```text
Malware Detected
```

Options:

* Block
* Ignore

For safe USB:

```text
No Malware Found
```

Option:

* Finish

---

## Edge AI Implementation

The project uses ONNX Runtime for local AI inference.

Why Edge AI?

* All predictions occur locally
* No cloud dependency
* No internet required
* Reduced latency
* Faster execution
* Improved privacy

Traditional Flow:

```text
Device → Cloud → Prediction
```

Project Flow:

```text
Device → ONNX Runtime → Prediction
```

---

## Repository Structure

```text
Edge-AI-Based-Faster-USB-Intrusion-Detector

├── 01_SignatureDataset
├── 02_SignatureModel
├── 03_SignProjNoGUI
├── 04_SignatureProject
├── 05_addingONNXruntime
├── 06_behaviorModel
├── 07_hybridScanning
├── edgeAI_USB_id&ps.py
├── bestAIModel.onnx
├── behavModel.onnx
└── README.md
```

---

## Future Enhancements

* USB reputation logging
* Previously scanned USB recognition
* Continuous monitoring for multiple USB devices
* Detailed threat reports
* Threat severity scoring
* Larger malware datasets
* Advanced behavior analytics
* Real-time logging dashboard

---

## Learning Outcomes

This project demonstrates practical implementation of:

* Machine Learning
* Edge AI
* ONNX Runtime
* USB Monitoring
* Malware Detection
* Feature Engineering
* Entropy Analysis
* Multithreading
* GUI Development
* Cybersecurity Concepts

---

## Author

Priyanshu Jugran<br>
CS Student - ML Enthusiast

---

## Conclusion

This project successfully combines Signature-Based Detection, Behavior-Based Detection, and Edge AI technologies into a unified USB security framework. By performing all analysis locally using ONNX Runtime, the system provides a lightweight, fast, and offline-capable solution for detecting USB-borne threats while maintaining user privacy and low system overhead.
