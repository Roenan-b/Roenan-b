# Roenan Bingle

Software engineer focused on security engineering, binary analysis, and mission-critical systems.

I study Software Engineering at the University of Arizona (B.S., expected May 2027) and am a member of the Department of Defense's Defense Civilian Training Corps (DCTC), Cohort 2027. My work sits where software meets the systems it controls: firmware and embedded controllers, binary-level vulnerability analysis, adversarial testing of tool-using agents, and zero-trust architectures for sensitive data.

---

## Tech Stack

**Languages**  
![C](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white) ![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**Frameworks and Data**  
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=white) ![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white)

**Infrastructure and Tooling**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black) ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

**Embedded**  
![Arduino](https://img.shields.io/badge/Arduino-00878F?style=for-the-badge&logo=arduino&logoColor=white) ![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white) ![PlatformIO](https://img.shields.io/badge/PlatformIO-F5822A?style=for-the-badge&logo=platformio&logoColor=white)

---

## Experience

**Space Systems Command, Los Angeles Air Force Base**  
*Intern, FORGE program (via DCTC)* · Summer 2026  
Placed with a Space Systems Command engineering team aligned with my major.

**Air Lift Company**  
*Software Engineering Intern* · Summer 2023, Summer 2024
- **2024, Smart Hitch.** Led software for an aftermarket hitch-mounted sensing unit that drives an air-suspension system to keep a towing vehicle level. Embedded C/C++ on Arduino-class hardware, CAN communication with the suspension, sensor processing and control logic, UML design, and testing.
- **2023, Compressor Tester.** Designed and built a test station for warranty-return air compressors by repurposing an obsolete leak-test fixture. Owned requirements, UML design, implementation, and deployment; the station supports all relevant compressor models and cut returned-unit processing time by roughly 50%.

---

## Research

### Binary Vulnerability Analysis (BVA) · *Directed research, Aug 2025 to present*
Vulnerability detection that works directly on compiled ELF binaries, with no source code, build system, or symbols required. The pipeline recovers control-flow and data-dependence graphs from AArch64 and ARM Cortex-M binaries, fuses them into a single program graph, locates candidate vulnerability anchors with a set of detector classes (dangerous API use, unsafe memory patterns, and similar), slices the graph around each anchor into an ordered code gadget, and classifies each gadget with a CWE category and an evidence-grounded justification. A deterministic rule-based classifier takes over when the model endpoint is unavailable. Evaluation uses the NIST SARD Juliet test suite. Built in Python on angr. *Repository private; manuscript in progress.*

### Prompt Injection in MCP Tool-Using Agents · *Course research, Jan 2026 to May 2026*
A test harness for measuring how LLM agents behave when attacker-controlled instructions arrive through Model Context Protocol (MCP) tool outputs rather than through the user. The **Mission Briefing Assistant** connects an agent to filesystem, Git, and SQLite MCP servers over a synthetic threat-intelligence workspace, then plants poisoned content in reports, database rows, and commit history. A scripted matrix of attack cases (output suppression, false attribution, confidence manipulation, cross-tool bridging, memory poisoning, OAuth token leakage and scope escalation, and others) runs in baseline and guardrailed modes, with JSONL logs and CSV summaries for comparison. Attack cases were derived from a STRIDE threat model of the agent-tool trust boundary.
[`mission-briefing-assistant`](https://github.com/Roenan-b/MCP_Clone/tree/main/mission-briefing-assistant) · Python, MCP, OAuth 2.0

---

## Projects

### Mission: Zero-Trust · *ENGR 498 capstone, in progress*
Proof of concept for location-bounded, ephemeral access to sensitive medical records, built by a multidisciplinary team (software, electrical and computer, biomedical, and systems engineering). An authorized user redeems a single-use access code for a short-lived cryptographic session, and a synthetic patient record is viewable only while the device is physically inside a designated room. Room presence is established by authenticated BLE beacons on ESP32 hardware. Each session's keys live only in a short-lived, locked-down processing container; leaving the room, losing the signal, or hitting the session timeout revokes the session and destroys the keys, so any remaining ciphertext is unrecoverable (cryptographic erasure). Python/FastAPI services, Docker Compose, an Android client, ESP32 firmware, and a suite of adversarial security tests (replay, forgery, session hijack, geofence spoofing, fault injection). Uses synthetic data only. *Repository private.*

### cc-hub
Multi-agent orchestration platform for [Claude Code](https://code.claude.com). A lead session plans a project, proposes the team it needs, and after approval starts and coordinates worker sessions (engineers, researchers, reviewers, writers), each running in tmux and, for engineers, in an isolated git worktree. A Node.js hub provides a web and mobile control surface with approval cards, a Postgres-backed task board with dependencies and independent review, full message history with search, a watchdog for stalled sessions, and an Obsidian vault for plans, decisions, and reports. One-command install on Linux and Windows (WSL2); runs locally and starts at boot.
[`cc-hub`](https://github.com/Roenan-b/cc-hub) · Node.js, PostgreSQL, tmux, MCP

### The Soil Watch
Soil-moisture monitoring system. Battery-powered ESP32 sensor nodes in weather-resistant enclosures report readings to a Supabase (PostgreSQL) backend, and a Next.js dashboard shows moisture readings for each plant.
[`The-Soil-Watch`](https://github.com/Roenan-b/The-Soil-Watch) · ESP32, C++, Supabase, React, Next.js

### Missile / Rocket Simulator
Simulation of flight trajectory and system behavior for aerospace applications.

### Pharmacy Management System · *SFWE 301 team project*
Requirements and design for a pharmacy management system covering inventory, prescriptions, sales, and insurance claims, with a system context model. Includes a Java reporting module that produces operational reports (inventory levels, sales, drug usage, turnover, insurance claims, fill history, user activity) from structured data exports. *Repository private.*

### Modified Go Fish
Two-player Go Fish (user versus computer) in C on a reduced 36-card deck, with the deck and hands modeled as linked lists, a randomized shuffle, and turn logic for requests, draws, and completed books.
[`Modified-Go-Fish-Game`](https://github.com/Roenan-b/Modified-Go-Fish-Game) · C

### Air Lift internship work
[`Smart-Hitch`](https://github.com/Roenan-b/Smart-Hitch) (overview only; source is proprietary) · [`Compressor-Tester`](https://github.com/Roenan-b/Compressor-Tester) (Arduino source, revision history, and validation data)

---

## Engineering Practice

| Area | |
|---|---|
| **Security** | Threat modeling (STRIDE), binary analysis, reverse engineering, concolic execution, adversarial testing of LLM agents, applied cryptography, NIST SP 800-53, RMF |
| **Analysis tooling** | angr, Ghidra, static and dynamic analysis, AArch64 cross-compilation and QEMU emulation |
| **Hardware and protocols** | Verilog, CAN bus, BLE |
| **Process** | Requirements engineering, UML, verification and test planning |

---

## GitHub Activity

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=Roenan-b&card_width=467&show_icons=true&hide_border=true&hide_rank=true&hide=stars,issues,contribs&include_all_commits=true&count_private=true&theme=github_dark">
  <img alt="GitHub stats" src="https://github-readme-stats.vercel.app/api?username=Roenan-b&card_width=467&show_icons=true&hide_border=true&hide_rank=true&hide=stars,issues,contribs&include_all_commits=true&count_private=true&theme=default">
</picture>
<br>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=Roenan-b&layout=compact&hide=jupyter%20notebook,html&langs_count=8&card_width=467&hide_border=true&theme=github_dark">
  <img alt="Most used languages" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Roenan-b&layout=compact&hide=jupyter%20notebook,html&langs_count=8&card_width=467&hide_border=true&theme=default">
</picture>

---

## Affiliations

- Defense Civilian Training Corps (DCTC), Cohort 2027
- National Society of Leadership and Success (NSLS)

## Contact

[LinkedIn](https://www.linkedin.com/in/roenan/)
