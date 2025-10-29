# Spotify Follow/Unfollow Bot

This project automates follow and unfollow actions on Spotify using Android real devices and emulators, orchestrated from the Appilot dashboard. It removes repetitive tapping, searching, and profile navigation while preserving human-like behavior to reduce detection. Teams use it to scale audience growth, experiment with engagement strategies, and maintain clean, compliant workflows at volume.

<p align="center">
  <a href="https://Appilot.app" target="_blank">
    <img src="media/appilot-baner.png" alt="Appilot Banner" width="100%">
  </a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20Appilot%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:support@appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>


<p align="center"> 
   Created by Appilot, built to showcase our approach to Automation!<br>
   <strong>If you are looking for custom Spotify Follow/Unfollow Bot, you've just found your team — Let’s Chat.👆👆</strong>
</p>

## Introduction
**What it does:** Automates Spotify account follow/unfollow flows — artists, users, and playlists — across multiple Android devices or emulators with human-like gestures, delays, and navigation.

**Problem it solves:** Manual follow management is slow, error-prone, and hard to scale without risking bans. This bot standardizes the flow, adds safety controls, and operates concurrently.

**Benefit:** Achieve predictable growth experiments, manage churn/unfollow cycles, and keep action rates within safe thresholds while logging every action for audit.

### Automating Spotify Engagement Cycles
- Safely executes targeted follow and scheduled unfollow waves aligned to daily/weekly caps.
- Works on real devices and emulators with randomized inputs, swipes, and dwell timing.
- Operates with rotating proxies, fingerprints, and per-account isolation to lower detection.
- Centralized runs, logs, and retry policies from Appilot’s orchestration dashboard.

## Core Features
- **Real Devices and Emulators:** Run on physical Android phones or emulators (Bluestacks/Nox), including farm-mode parallelism with per-device isolation.
- **No-ADB Wireless Automation:** Control devices via Wi-Fi (scrcpy/adb-over-TCP) and Accessibility/UI Automator pipelines to minimize cable reliance and port juggling.
- **Mimicking Human Behavior:** Randomized tap radii, scrolling curves, jittered delays, page-dwell variance, and occasional backtracks to match human patterns.
- **Multiple Accounts Support:** Segregated sessions, encrypted creds, per-account rate limits, and independent task queues to avoid cross-contamination.
- **Multi-Device Integration:** Horizontal scaling to hundreds of devices with coordinated schedules and health checks (battery, latency, foreground app).
- **Exponential Growth for Your Account:** Cadenced follow strategies, niche targeting, and controlled unfollow cycles to iterate towards compounding reach.
- **Premium Support:** Priority issue triage, device-farm tuning, and enterprise SLAs for uptime and throughput.
- **Smart Targeting & Lists:** Import artist/user/playlist targets via CSV/Google Sheets; de-duplication and historical memory avoid redundant actions.
- **Stealth & Fingerprinting:** MultiLogin/AdsPower profiles, stable device IDs, and configurable language/locale to lower anomaly signals.
- **Queue, Retry & Backoff:** Idempotent task queue with exponential backoff, cool-down periods, soft/hard retries, and dead-letter handling.

**Additional Feature Set (Table)**

| Feature | Description |
|---|---|
| **Proxy Rotation & Geo-Targeting** | Assign mobile/residential proxies per account, rotate by policy, and map geos to match expected audience regions. |
| **CAPTCHA Handling & Fallbacks** | Detects challenge patterns and routes flows to solver/fallback queues; pauses risky accounts and annotates evidence. |
| **Scheduler & Windowing** | Define daily action windows, caps, and quiet hours; stagger device start to avoid synchronized bursts. |
| **Audit Logs & Telemetry** | Structured logs (JSON), per-action screenshots (optional), Prometheus metrics, and Grafana-ready exporters. |
| **Policy Safeguards** | Hard caps, cooling timers, domain allowlists, and immediate kill-switch from the dashboard for safe halts. |
| **Insights & A/B Experiments** | Compare target lists, cadences, and timing to find optimal strategies with exportable CSV reports. |

</p>
<p align="center">
  <a href="https://bitbash.dev" target="_blank">
    <img src="spotify-follow-unfollow-bot-architecture.png" alt="spotify-follow-unfollow-bot-architecture" width="95%">
  </a>
</p>

## How It Works (must)
1. **Input or Trigger** — The automation is triggered through the Appilot dashboard, where the user sets tasks like “follow artists from list A” or “unfollow users not followed back after 14 days” on Android devices or emulators.  
2. **Core Logic** — Appilot drives the device UI via UI Automator/Accessibility (or ADB where applicable): opens Spotify, searches targets, navigates to profiles, taps Follow/Unfollow, and records outcomes with screenshots and logs.  
3. **Output or Action** — The system executes the queued actions and returns a run report (success/fail, reasons, screenshots), updating per-account quotas and history.  
4. **Other functionalities** — Retry/backoff, error classification (UI changes, network, challenge), structured logging, parallel processing, and health monitoring are configurable in the dashboard.

## Tech Stack (must)
- **Language:** Kotlin, Java, JavaScript, Python  
- **Frameworks:** Appium, UI Automator, Espresso, Robot Framework, Cucumber  
- **Tools:** Appilot, Android Debug Bridge (ADB), Appium Inspector, Bluestacks, Nox Player, Scrcpy, Firebase Test Lab, MonkeyRunner, Accessibility  
- **Infrastructure:** Dockerized device farms, Cloud-based emulators, Proxy networks, Parallel Device Execution, Task Queues, Real device farm

## Directory Structure (must)
```
	spotify-follow-unfollow-bot/
	│
	├── src/
	│   ├── python/
	│   │   ├── main.py
	│   │   ├── orchestrator/
	│   │   │   ├── scheduler.py
	│   │   │   ├── queue.py
	│   │   │   └── backoff.py
	│   │   ├── device/
	│   │   │   ├── adb_client.py
	│   │   │   ├── ui_automator.py
	│   │   │   └── accessibility.py
	│   │   ├── spotify/
	│   │   │   ├── flows_follow.py
	│   │   │   ├── flows_unfollow.py
	│   │   │   └── detectors.py
	│   │   └── utils/
	│   │       ├── logger.py
	│   │       ├── proxy_manager.py
	│   │       ├── fingerprint.py
	│   │       └── screenshots.py
	│   └── kotlin/
	│       ├── build.gradle.kts
	│       └── app/
	│           ├── src/main/AndroidManifest.xml
	│           └── src/main/java/dev/appilot/bot/AccessibilityService.kt
	│
	├── config/
	│   ├── settings.yaml
	│   ├── device_pool.yaml
	│   ├── targets.csv
	│   └── credentials.env
	│
	├── dashboards/
	│   ├── grafana/
	│   │   └── spotify-bot.json
	│   └── prometheus/
	│       └── prometheus.yml
	│
	├── logs/
	│   ├── runs/
	│   └── screenshots/
	│
	├── output/
	│   ├── reports/
	│   │   ├── run-YYYYMMDD.csv
	│   │   └── experiment-metrics.csv
	│   └── artifacts/
	│
	├── docker/
	│   ├── Dockerfile
	│   └── docker-compose.yml
	│
	├── tests/
	│   ├── unit/
	│   └── e2e/
	│
	├── requirements.txt
	└── README.md
```
## Use Cases (must)
- **Growth teams** use it to follow targeted artist/user segments, so they can test audience growth hypotheses without manual effort.  
- **Agencies** use it to manage multi-account follow/unfollow cadences, so they can standardize safe operating limits across clients.  
- **Ops engineers** use it to run large device farms at off-peak hours, so they can maximize throughput within rate caps.  
- **Analysts** use it to A/B target lists and schedules, so they can discover which cadences yield the best retention.

## FAQs
**How do I configure this automation for multiple accounts?**  
Add each account in `credentials.env` (or vault), map to a device slot in `device_pool.yaml`, and set per-account caps in `settings.yaml`. The scheduler assigns jobs while respecting isolation and rate limits.

**Does it support proxy rotation or anti-detection?**  
Yes. Assign residential/mobile proxies per account via `proxy_manager.py`, integrate MultiLogin/AdsPower profiles, and tune fingerprint parameters in `fingerprint.py`.

**Can I schedule it to run periodically?**  
Use `scheduler.py` to define windows (e.g., 9:00–11:00, 18:00–21:00), daily caps, and quiet hours. Staggered starts and randomized delays are built-in.

**What targets can I follow or unfollow?**  
Import artists, users, or playlist owner profiles via `targets.csv`. The bot deduplicates and tracks success history to avoid repeats.

**What happens on UI changes or errors?**  
Detectors flag layout changes; retries/backoff kick in. Items causing repeated failures move to a dead-letter queue for review with screenshots.

## Performance & Reliability Benchmarks (must)
- **Execution Speed:** 100–180 follow/unfollow actions per device per hour (humanized pacing, jittered delays).  
- **Success Rate:** **95%** end-to-end action confirmation on stable network/device farms.  
- **Scalability:** Proven patterns for **300–1,000** Android devices with sharded queues and proxy pools.  
- **Resource Efficiency:** Low CPU on orchestrator (<20% avg), bounded memory via streaming logs and screenshot throttling.  
- **Error Handling:** Categorized retries, exponential backoff, cooldown timers, device health watchdogs, and on-demand kill switch.

##
<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
</p>
