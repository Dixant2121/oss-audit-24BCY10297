# oss-audit-24BCY10297

## The Open Source Audit — Apache HTTP Server

**Student:** Dixant Paptwan
**Registration Number:** 24BCY10297
**Course:** Open Source Software (OSS NGMC)
**Chosen Software:** Apache HTTP Server

---

## About This Project

This repository contains the shell scripts and supporting materials for the Open Source Audit capstone project. The project is a structured audit of the **Apache HTTP Server** — one of the most influential open-source projects in the history of the web, powering approximately 30% of all websites globally.

The audit covers the origin story and philosophy of Apache, its license (Apache License 2.0), its Linux footprint, its place in the FOSS ecosystem, and a comparison with proprietary alternatives.

---

## Repository Contents

```
oss-audit-24BCY10297/
├── README.md
├── script1_system_identity.sh
├── script2_package_inspector.sh
├── script3_disk_auditor.sh
├── script4_log_analyzer.sh
└── script5_manifesto_generator.sh
```

---

## Scripts Overview

### Script 1 — System Identity Report (`script1_system_identity.sh`)
Displays a welcome screen with key information about the Linux system: distribution name, kernel version, logged-in user, home directory, system uptime, current date/time, and the OS license.

**Concepts used:** Variables, `echo`, command substitution (`$()`), output formatting.

---

### Script 2 — FOSS Package Inspector (`script2_package_inspector.sh`)
Checks whether Apache HTTP Server is installed on the system, retrieves version and license details, and prints a philosophy note about the software using a `case` statement. Supports both Debian-based (`dpkg`/`apt`) and RPM-based (`rpm`/`yum`) systems.

**Concepts used:** `if-then-else`, `case` statement, `rpm -qi` / `dpkg -l`, pipes with `grep`.

---

### Script 3 — Disk and Permission Auditor (`script3_disk_auditor.sh`)
Loops through a list of important system directories (`/etc`, `/var/log`, `/home`, `/usr/bin`, `/tmp`, `/var/www`, Apache config dirs) and reports the permissions, owner, group, and disk usage of each. Includes a dedicated section for Apache's configuration and log directories.

**Concepts used:** `for` loop, `du`, `ls -ld`, `awk`, `cut`.

---

### Script 4 — Log File Analyzer (`script4_log_analyzer.sh`)
Reads Apache log files (or any log file passed as an argument) line by line, counts occurrences of a keyword (`error`, `404`, `500`, etc.), and prints a summary with the last 5 matching lines. Falls back to scanning common Apache log paths if no file is specified.

**Concepts used:** `while read` loop, `if-then`, counter variables, command-line arguments (`$1`, `$2`).

---

### Script 5 — Open Source Manifesto Generator (`script5_manifesto_generator.sh`)
Interactively asks the user three questions, then generates a personalised open-source philosophy statement inspired by the Apache Way. The output is saved to a timestamped `.txt` file and previewed in the terminal.

**Concepts used:** `read` for user input, string concatenation, writing to a file with `>` and heredoc (`<<EOF`), `date` command, input validation loop.

---

## How to Run the Scripts

### Prerequisites

- A Linux system (Ubuntu, Debian, Fedora, RHEL, or similar)
- Bash shell (`bash --version` to verify)
- For Script 2: `apache2` or `httpd` package (optional — the script handles the case where it is not installed)
- For Script 4: Apache must be installed and have generated log files, OR you can pass any log file as an argument

### Setup

Clone the repository and make all scripts executable:

```bash
git clone https://github.com/<your-username>/oss-audit-24BCY10927.git
cd oss-audit-24BCY10297
chmod +x *.sh
```

### Running Each Script

**Script 1 — System Identity Report**
```bash
./script1_system_identity.sh
```

**Script 2 — FOSS Package Inspector**
```bash
./script2_package_inspector.sh
```

**Script 3 — Disk and Permission Auditor**
```bash
./script3_disk_auditor.sh
```
> Some directories (e.g. `/var/log`) may require `sudo` for accurate size reporting:
> ```bash
> sudo ./script3_disk_auditor.sh
> ```

**Script 4 — Log File Analyzer**

Automatic mode (scans for Apache logs):
```bash
./script4_log_analyzer.sh
```

Manual mode (specify a log file and optional keyword):
```bash
./script4_log_analyzer.sh /var/log/syslog error
./script4_log_analyzer.sh /var/log/apache2/access.log 404
```

**Script 5 — Open Source Manifesto Generator**
```bash
./script5_manifesto_generator.sh
```
Follow the three prompts. Your manifesto will be saved as `manifesto_<username>_<timestamp>.txt` in the current directory.

---

## Dependencies

| Script | Dependencies |
|--------|-------------|
| Script 1 | `uname`, `whoami`, `uptime`, `lsb_release` or `/etc/os-release` |
| Script 2 | `dpkg` (Debian/Ubuntu) or `rpm` (RHEL/Fedora) |
| Script 3 | `ls`, `du`, `awk`, `cut` |
| Script 4 | `grep`, standard log files or Apache HTTP Server |
| Script 5 | `date`, `hostname`, `whoami` |

All dependencies are standard utilities present on any Linux distribution.

---

## License

This project was created for academic purposes as part of the Open Source Software course.
The shell scripts in this repository are released under the **MIT License**.

The Apache HTTP Server — the subject of this audit — is licensed under the **Apache License 2.0**.
See: [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)

---

*Open Source Software Course | VIT | 2024–25*
