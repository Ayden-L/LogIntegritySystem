# Log Integrity System

<h2>Description</h2>
Designed and implemented a secure log server using Python to enforce integrity in a distributed logging system. Incorporated cryptographic hashing, proof-of-work (PoW), and log chain validation to simulate real-world log security practices and tamper resistance.
<br />

<h2> Technologies Used </h2>

- Python 3.8+
- hashlib for SHA-256 hashing
- datetime for timestamping
- Lightweight and no third-party libraries included

<h2> Key Features </h2>

- Tamper-evident logging: each log entry includes a cryptographic hash of the previous entry to form an immutable chain
- Integrity Verification: quickly identify the exact point of tampering or corruption within the log file
- Cryptographic Hashing (SHA-256): used for strong integrity checks

<h2> Implementation Details </h2>

* Built a client-server logging architecture using sockets that securely appends log entries with embedded hash values to ensure tamper-evident storage
* Implemented a proof-of-work (PoW) to rate-limit and authenticate log submissions using a leading-zero SHA-256 hash constraint (22-bit PoW requirement)
* Created a hash-linked log chain by storing only the base64-encoded tail of each log entry's SHA-256 hash and appending it to the next message, enforcing forward integrity
* Developed a verification tool (checklog.py) to recursively validate the integrity of logs and compare against a loghead pointer for head verification
* Integrated error handling and security validation to prevent malformed logs, missing file states, or PoW bypass attempts

<h2> Security Use Case </h2>
This project is relevant for:

* SOC analysts verify the integrity of log alerts
* IT professionals auditing configuration change history
* Blue teamers performing forensics after potential breaches
* Security engineers designing secure log pipelines

<h2> Future Feature Enhancements </h2>

* Timestamp validation
* Digital signatures for entry authorization
* Integration with syslog
* Web dashboard for visualization
