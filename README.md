# -Endpoint-Protection-and-Ransomware-Defence-for-Medicare-Systems
# Endpoint Protection and Ransomware Defence Application for Medicare Systems

**A lightweight, scalable, multi-layered cybersecurity solution tailored for healthcare infrastructures, offering real-time endpoint protection, ransomware detection, automated incident response, and secure backups.**

***

## Table of Contents
- [Project Overview](#project-overview)  
- [Key Features](#key-features)  
- [Technology Stack](#technology-stack)  
- [Architecture & Modules](#architecture--modules)  
- [Prerequisites](#prerequisites)  
- [Installation & Setup](#installation--setup)  
- [Usage](#usage)  
- [Configuration](#configuration)  
- [Folder Structure](#folder-structure)  
- [Testing](#testing)  
- [Contributing](#contributing)  
- [License](#license)  
- [Authors & Acknowledgements](#authors--acknowledgements)  

***

## Project Overview  
Healthcare organizations face escalating ransomware and malware threats targeting sensitive patient data. This application combines Endpoint Detection and Response (EDR), Intrusion Detection Systems (IDS), machine learning–based anomaly detection, real-time alerts, and encrypted backup/recovery to safeguard Medicare systems against evolving cyberattacks while ensuring HIPAA compliance and minimal system overhead.

***

## Key Features
- **Real-time Endpoint Monitoring**: Tracks file I/O, processes, and network patterns.  
- **Ransomware & Malware Detection**: Hybrid signature- and behavior-based detection with AI/ML models.  
- **Automated Incident Response**: Endpoint isolation, alerting, and on-demand or automatic recovery.  
- **Network Intrusion Detection**: Suricata‐powered traffic analysis for anomaly detection.  
- **Encrypted Cloud Backup & Recovery**: AES-256 encryption, versioning, and policy-driven sync to AWS/GCS.  
- **Admin Dashboard**: React.js interface with real-time alerts, visual charts, and policy configuration.  

***

## Technology Stack
- **Languages**: Python, JavaScript  
- **Frontend**: React.js  
- **Backend & ML**: Flask/Django (or FastAPI), Scikit-learn, TensorFlow  
- **Database**: PostgreSQL  
- **Security Libraries**: PyCryptodome, VirusTotal API  
- **Network Analysis**: Suricata, Wireshark  
- **Cloud**: AWS (EC2, S3), Google Cloud Storage  
- **CI/CD**: GitHub Actions (optional)  

***

## Architecture & Modules
1. **Agent Module**  
   - Process Monitoring  
   - File Activity Tracker  
   - Network Anomaly Detector  

2. **Server Module**  
   - Signature-based Detection  
   - Machine Learning Behavioral Analysis  
   - Incident Response Manager  

3. **Dashboard Module**  
   - Real-time Alerts  
   - Visualization Charts  
   - Policy Configuration  

4. **Backup Module**  
   - Periodic Cloud Sync  
   - File Versioning  
   - Encrypted Storage  

5. **Security Mechanisms**  
   - Real-Time File Integrity Monitoring  
   - AES-256 Encryption  
   - Endpoint Isolation  
   - Role-based Access Control  

***

## Prerequisites
- Python 3.8+  
- Node.js & npm  
- PostgreSQL  
- AWS & GCP credentials (for backup module)  
- Suricata installed on the server/agent machines  

***

## Installation & Setup

1. **Clone the repository**  
   ```bash
   git clone https://github.com/<your-username>/medicare-epdr.git
   cd medicare-epdr
   ```

2. **Backend Setup**  
   ```bash
   cd server
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Database Migration & Seed**  
   ```bash
   psql -U postgres -c "CREATE DATABASE epdr_db;"
   flask db upgrade
   flask seed-data
   ```

4. **Frontend Setup**  
   ```bash
   cd ../dashboard
   npm install
   npm run build
   ```

5. **Configure Environment Variables**  
   Create a `.env` file in `server/`:
   ```ini
   FLASK_ENV=production
   SECRET_KEY=<your-secret-key>
   DATABASE_URL=postgresql://postgres:password@localhost/epdr_db
   AWS_ACCESS_KEY_ID=<your-access-key>
   AWS_SECRET_ACCESS_KEY=<your-secret-key>
   GCS_CREDENTIALS_PATH=/path/to/gcs-key.json
   ```

6. **Run Services**  
   ```bash
   # Start the threat intelligence server
   cd server
   flask run --host=0.0.0.0 --port=5000

   # Start the frontend dashboard (development)
   cd ../dashboard
   npm start
   ```

***

## Usage
1. **Install the Endpoint Agent** on each endpoint machine:
   ```bash
   cd agent
   python setup.py install
   epdr-agent --start
   ```
2. **Access the Dashboard**  
   Open your browser to `http://<server-ip>:3000` to monitor endpoints, view alerts, and configure policies.

3. **Simulate an Attack**  
   Use provided scripts in `tests/` to generate simulated ransomware file operations and observe detection, isolation, and recovery.

***

## Configuration
- **Policy Management**: Define exclusion lists, alert thresholds, backup schedules, and endpoint groups via the dashboard.  
- **ML Model Retraining**: Store new labeled logs in `server/data/training/` and run:
  ```bash
  python server/train_model.py --dataset ./data/training/ --output ./models/
  ```

***

## Folder Structure
```
medicare-epdr/
├── agent/                  # Endpoint agent code
├── server/                 # Threat intelligence server & ML models
│   ├── app/
│   ├── data/
│   └── models/
├── dashboard/              # React.js admin dashboard
├── tests/                  # Attack simulation & unit tests
├── .gitignore
├── LICENSE
└── README.md
```

***

## Testing
- **Unit Tests**:  
  ```bash
  cd server
  pytest
  ```
- **Integration Tests**:  
  Scripts in `tests/integration/` simulate multi-endpoint attacks and backup workflows.

***

## Contributing
1. Fork the repository.  
2. Create a feature branch: `git checkout -b feature/YourFeature`.  
3. Commit your changes: `git commit -m "Add YourFeature"`.  
4. Push to your fork: `git push origin feature/YourFeature`.  
5. Open a Pull Request against `main`.  

Please follow the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md).

***

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

***

## Authors & Acknowledgements
- **M. Vinay Kumar** (9921004447)  
- **M. Madhan** (9921004421)  
- **M. Mohan Krishna Reddy** (9921004428)  
- **K. Divya** (9921004178)  
- **Supervisors**: Dr K Kartheeban, Dr N. Suresh Kumar  

Thanks to the **Computer Science & Engineering Department** at Kalasalingam Academy of Research and Education for guidance and support.

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/59222932/7d602f4f-2948-4e01-b6a5-3e04b52d7f92/CAPSTONE_Final_Report.pdf)
