# Trustistics – Blockchain-Powered Cold-Chain Provenance

> A cold-chain provenance platform that combines IoT telemetry, cryptographic verification, and blockchain technology to improve the integrity and traceability of temperature-sensitive shipments.

![Trustistics Banner](https://github.com/avcusnatsova/Trustistics/raw/main/trustistics_banner_v2_1777534273700.png)

---

## Overview

**Trustistics** is a supply-chain provenance platform designed to improve transparency and data integrity across temperature-sensitive logistics.

The system connects simulated IoT telemetry with a blockchain-backed verification layer to record shipment conditions and document handoffs in a tamper-evident manner.

The platform is designed around the principle that critical cold-chain data should be generated from sensor telemetry rather than relying entirely on manual entry.

---

## Key Features

### Immutable Provenance

Sensor readings and shipment documents can be associated with cryptographic hashes and anchored to the blockchain, providing a verifiable record of stored information.

### Automated IoT Telemetry

The system includes an IoT telemetry simulator that generates temperature readings for shipments, reducing reliance on manually entered sensor data during testing.

### Temperature Breach Detection

Shipment-specific temperature thresholds are monitored to identify potential cold-chain breaches and calculate associated risk.

### QR-Based Verification

QR codes provide a convenient way to access shipment verification information and review the recorded cold-chain history.

### Multi-Role Dashboards

The platform provides role-specific interfaces for:

* Administrators
* Manufacturers
* Warehouse Operators
* Drivers

### Document Verification

Important logistics documents such as:

* Certificates of Origin
* Bills of Lading
* Quality Certificates

can be associated with cryptographic hashes to support integrity verification.

---

## Architecture

```text
                         ┌─────────────────────┐
                         │      IoT Sensors    │
                         │   / Telemetry Sim   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │      FastAPI        │
                         │       Backend       │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼───────────────┐
                    ▼               ▼               ▼
             ┌────────────┐ ┌────────────┐ ┌──────────────┐
             │  MongoDB   │ │ Blockchain │ │ Risk / Breach│
             │  Database  │ │  Contracts │ │   Detection  │
             └────────────┘ └────────────┘ └──────────────┘
                    │               │               │
                    └───────────────┼───────────────┘
                                    ▼
                         ┌─────────────────────┐
                         │    React Frontend   │
                         │ Dashboards + QR UI  │
                         └─────────────────────┘
```

---

## Technology Stack

### Frontend

* React
* TypeScript
* Vite
* Tailwind CSS
* GSAP

### Backend

* Python
* FastAPI
* Pydantic

### Database

* MongoDB

### Blockchain

* Solidity
* Hardhat
* Web3.py

### IoT

* Python-based telemetry simulation

---

## System Workflow

```text
Shipment Created
       ↓
IoT Telemetry Generated
       ↓
Temperature Data Received
       ↓
Threshold Validation
       ↓
Risk / Breach Detection
       ↓
Cryptographic Hash Generated
       ↓
Blockchain Anchoring
       ↓
Data Stored for Verification
       ↓
Dashboard / QR Verification
```

---

## Security & Data Integrity

Trustistics uses cryptographic hashing and blockchain anchoring to provide a tamper-evident verification mechanism.

### Zero-Trust Telemetry

Critical shipment telemetry is designed to originate from sensor-based data rather than unrestricted manual input.

### Cryptographic Verification

Shipment data and documents can be represented using cryptographic hashes. The resulting hash can be compared against the anchored record to identify unauthorized modifications.

### Blockchain Anchoring

Blockchain storage is used as a verification layer for important shipment records, providing an independently verifiable reference for data integrity.

---

## Getting Started

### Prerequisites

Install the following before running the application:

* Node.js 18+
* Python 3.10+
* MongoDB or MongoDB Atlas
* Hardhat
* Git

---

### 1. Clone the Repository

```bash
git clone https://github.com/avcusnatsova/Trustistics.git
cd Trustistics
```

---

### 2. Backend Setup

```bash
cd backend

python -m venv venv
```

#### Windows

```bash
venv\Scripts\activate
```

#### macOS / Linux

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Configure the environment variables using the provided environment configuration template.

Start the backend:

```bash
uvicorn main:app --reload
```

---

### 3. Frontend Setup

Open a new terminal:

```bash
cd frontend
npm install
npm run dev
```

The Vite development server will provide the local frontend URL.

---

### 4. Blockchain Setup

Navigate to the blockchain directory:

```bash
cd blockchain
npm install
```

Start the local Hardhat network if required:

```bash
npx hardhat node
```

Deploy the contracts:

```bash
npx hardhat run scripts/deploy.js --network localhost
```

Configure the resulting contract/RPC information in the backend environment configuration.

---

### 5. Run the IoT Simulator

The project includes a Python-based IoT simulator for generating shipment telemetry.

Example:

```bash
python iot_simulator.py SHP-3601 -72
```

This simulates telemetry for the specified shipment.

---

## Project Structure

```text
Trustistics/
│
├── backend/
│   ├── routes/
│   ├── services/
│   ├── models/
│   └── main.py
│
├── frontend/
│   ├── src/
│   ├── components/
│   └── ...
│
├── blockchain/
│   ├── contracts/
│   ├── scripts/
│   └── ...
│
├── iot_simulator.py
│
├── qrcodes/
│
├── uploads/
│
├── README.md
└── LICENSE
```

---

## Use Cases

Trustistics can be applied to scenarios where maintaining the integrity and traceability of shipment conditions is important, including:

* Pharmaceutical logistics
* Food and beverage transportation
* Vaccine distribution
* Cold-storage facilities
* Temperature-sensitive manufacturing
* Multi-party supply chains

---

## Future Improvements

Potential improvements include:

* Integration with physical IoT hardware
* Real-time telemetry streaming
* Mobile-based shipment verification
* Advanced anomaly detection
* Multi-network blockchain support
* Cloud deployment
* Enhanced analytics and reporting
* Automated compliance reporting

---

## Learning Outcomes

Building Trustistics provided practical experience with:

* Full-stack web application development
* React and TypeScript
* FastAPI backend development
* MongoDB data persistence
* REST API design
* Smart contract development
* Blockchain integration
* Cryptographic hashing
* IoT telemetry simulation
* QR-based verification workflows
* Multi-role application design

---

## Team

**Trustistics Team**

GitHub: https://github.com/avcusnatsova/Trustistics

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](https://github.com/avcusnatsova/Trustistics/blob/main/LICENSE) file for details.
