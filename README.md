<p align="center">
  <img src="https://github.com/user-attachments/assets/701020ba-2b18-4bf0-805e-ee75a211d7ed" alt="MANTIS Logo" width="200"/>
</p>

<h1 align="center">🦗 MANTIS - Advanced System Monitor Suite</h1>

<p align="center">
  <strong>Monitoring All Network, Tasks & Integrated Systems</strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#screenshots">Screenshots</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#download">Download</a> •
  <a href="#contributing">Contributing</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.3.1-blue.svg" alt="Version">
  <img src="https://img.shields.io/badge/Python-3.8+-green.svg" alt="Python">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License">
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6.svg" alt="Platform">
</p>

---

## 📖 Overview

**MANTIS** (Monitoring All Network, Tasks, and Integrated Systems) is a powerful, comprehensive monitoring tool designed for **program analysis and behavior inspection**. Whether you're a security researcher, developer, or just curious about what applications do behind the scenes, MANTIS provides deep visibility into:

- 📁 **File System Activity** - Track every file creation, modification, deletion, and rename
- 🔄 **Process & Task Management** - Monitor process creation, termination, and parent-child relationships
- 🌐 **Network Communication** - Inspect TCP packets, payloads, and associated processes
- 💻 **System Resource Monitoring** - Real-time CPU, memory, and network usage tracking

> **⚠️ Important**: MANTIS requires **Administrator privileges** to function properly (required for network monitoring and full process inspection).

## ✨ Features

### 📁 File Monitor
- Real-time file system event tracking (create, delete, modify, rename, move)
- Filter events by filename, extension, or event type
- Save monitoring logs to JSON format
- Watch any directory recursively
- Path resolution with clickable folder selection

### 🔄 Process Monitor
- Live process creation and termination tracking
- Display parent-child process relationships
- Separate windows for active and terminated processes
- Real-time PID and process name tracking
- Chronological event logging with timestamps

### 🌐 Network Monitor
- Real-time TCP packet inspection using WinDivert
- Display source/destination IP addresses and ports
- View packet payloads (first 200 bytes)
- Filter by process name or IP address
- **Interactive network graph visualization** (requires Graphviz)
- Associate network traffic with specific processes
- Domain name resolution for IP addresses

### 💻 CPU Monitor (Qt-based)
- Real-time CPU and memory usage graphs
- Per-process resource monitoring
- Network throughput visualization (KB/s)
- Process search and filtering
- Detailed process metrics (memory MB, threads, status)
- Select any process to view its detailed CPU/Memory history

## 🖼️ screenshots

<p align="center">
  <img src="https://github.com/user-attachments/assets/7e31deea-5787-45c1-ab99-68b9d7552f2d" alt="Process Monitor" width="45%">
  <img src="https://github.com/user-attachments/assets/0db87f42-8c77-4808-a0af-d25005b14831" alt="Network Monitor" width="45%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/74d0e58e-cc00-446b-a952-535af7fc3d65" alt="Main Interface" width="90%">
</p>

## 🚀 Quick Start

### Prerequisites

- **Windows OS** (uses WinDivert for network monitoring)
- **Python 3.8+**
- **Administrator privileges**

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/Mr-Spect3r/MANTIS.git
cd MANTIS
```

2. **Install Python dependencies**

```pip install -r requirements.txt```

```
Required libraries:

psutil          # Process and system monitoring
pydivert        # Network packet capture (Windows)
watchdog        # File system monitoring
customtkinter   # Modern GUI framework
graphviz        # Network graph visualization
Pillow          # Image processing for graphs
pyqtgraph       # Real-time CPU graphs
PySide6         # Qt framework for CPU monitor
```

3. **Install Graphviz (required for network graphs)**

```
# Using winget (recommended)
winget install graphviz

# Or download from: https://graphviz.org/download/
```

4. **Configure Graphviz PATH**

```
Add C:\Program Files\Graphviz\bin to your system PATH

Verify installation: dot -V
```

# Running MANTIS

```bash
# Run with administrator privileges (auto-elevates)
python mantis.py
```

Or download the pre-compiled executable:
👉 Download <a href="https://github.com/Mr-Spect3r/MANTIS/releases/download/MANTIS/MANTIS.exe">MANTIS.exe


## 📚 How To Use

### 🗂️ File Monitoring
1. Click **"File Monitor"** from the main menu
2. Select a directory to monitor (or use current path)
3. Click **"Start Monitoring"**
4. Any file activity in that directory will be logged
5. Use filters to narrow down events:
   - **Filename** - Filter by filename pattern
   - **Format** - Filter by file extension
   - **Type** - Filter by event type (CREATED/DELETED/UPDATED/MOVED)
6. Save logs using the **"Save Log"** button

### 📊 Process Monitoring
1. Click **"Process Monitor"** from main menu
2. Four panels display:
   - 🟢 **Started Tasks** - Newly created processes
   - 🔴 **Closed Tasks** - Terminated processes
   - 📄 **Closed List** - Summary of terminated processes
   - 👤 **Parent Process** - Which process spawned each child
3. Monitor runs automatically until window is closed

### 🌐 Network Monitoring
1. Click **"Network Monitor"** from main menu
2. All TCP traffic is captured and displayed
3. Each packet shows:
   - Source/Destination IP and port
   - Associated process name and executable path
   - Payload data (first 200 bytes)
4. Apply filters:
   - **Process Filter** - Show only specific process traffic
   - **IP Filter** - Filter by IP address
5. Click **"Graph"** to generate an interactive network visualization

### 💻 CPU Monitoring
1. Click **"CPU Monitor"** from main menu
2. Real-time graphs show:
   - Overall CPU usage %
   - Overall Memory usage %
   - Network send/receive (KB/s)
3. Process table shows all running processes
4. Click any process to view:
   - Per-process CPU history
   - Per-process memory usage (MB)
5. Use search box to filter processes by name or PID

---

## 🛠️ Architecture

```
MANTIS/
├── mantis.py           # Main application (Tkinter GUI)
│   ├── MonitorApp      # Main window controller
│   ├── FileMonitorWindow    # File system monitoring
│   ├── TaskWindow           # Process monitoring
│   ├── NetworkMonitorWindow # Network packet capture
│   └── AboutWindow          # About information
├── cpumonitor.py       # Standalone CPU monitor (Qt)
└── requirements.txt    # Python dependencies
```

## 🛠️ Key Components

- **WinDivert Integration**: Low-level TCP packet capture and injection
- **Watchdog**: Cross-platform file system event monitoring
- **psutil**: Cross-platform system and process information
- **CustomTkinter**: Modern, customizable GUI components
- **PyQtGraph**: High-performance real-time plotting

---

## 🔒 Security & Permissions

MANTIS requires **Administrator privileges** because:

- Network packet capture requires raw socket access
- Process inspection may need elevated rights
- File system monitoring of protected directories

The application automatically requests elevation on startup using Windows ShellExecute.

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

- **Report bugs** - Open an issue on GitHub
- **Suggest features** - Submit ideas via Telegram or GitHub
- **Submit pull requests** - For bug fixes or improvements

### Development Setup

```bash
git clone https://github.com/Mr-Spect3r/MANTIS.git
cd MANTIS
pip install -r requirements.txt
# Make your changes
python mantis.py
```
