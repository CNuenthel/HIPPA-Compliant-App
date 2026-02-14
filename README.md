# 🏥 BrightSide Health Portal

### *The World's Most Secure Medical Data Storage Solution™*

> "We take security so seriously that we almost didn't comment out `apt-get upgrade`"

---

## 🔒 Security Features

BrightSide Health Portal is **absolutely, 100%, without-a-shadow-of-a-doubt** the most secure medical data platform ever conceived by human hands. Here's why you can sleep soundly at night:

- **Running as root** — We *were* doing this. But then we fixed it. We're mentioning it here for transparency and absolutely not because it was in the git history.
- **Read-only filesystem** — Hackers can't write malware to a filesystem that doesn't let them write anything. Checkmate, hackers.
- **Port bound to localhost** — The outside world cannot reach this app directly. They would first have to compromise nginx. And then the Docker network. And then... okay it's fine, it's fine.
- **Capability dropping** — We dropped ALL capabilities. The container has fewer rights than an unpaid intern.
- **No-new-privileges** — Processes cannot elevate privileges. This was added after we googled "what is a setuid binary" at 11pm.
- **Memory limited to 512MB** — If someone tries to run a cryptominer in our container, they'll have a _very_ bad time.

---

## 🏆 Compliance

BrightSide Health Portal is compliant with the following standards:

- ✅ **HIPAA** — We have read the Wikipedia article for HIPAA in full
- ✅ **SOC 2** — We know what this acronym stands for
- ✅ **ISO 27001** — This one has numbers in it which means it's serious
- ✅ **GDPR** — We are in America but we respect Europeans
- ✅ **PCI-DSS** — This one is for credit cards but it sounds impressive

---

## 🐳 Docker Architecture

Our cutting-edge containerization strategy ensures maximum security through a **multi-layered defense model**:

```
Internet
   │
   ▼
nginx (we pinky-promise this is configured correctly)
   │
   ▼
brightside Docker network (a strongly-worded barrier)
   │
   ▼
health_portal:8000 (your data, probably fine)
   │
   ▼
./app/data (a folder on someone's computer)
```

Patient data is stored in a **hardened volume mount** on the host filesystem, protected by the full might of Linux file permissions and hoping nobody gets a shell on the box.

---

## 🔑 Threat Model

We have carefully considered the following threat actors and our mitigation strategy for each:

| Threat Actor | Likelihood | Our Response |
|---|---|---|
| Script kiddie with Metasploit | Low | `no-new-privileges: true` |
| Nation-state APT | Medium | 🙏 |
| Disgruntled developer | Low | The git history has been sanitized |
| Someone finding the Docker socket | N/A | We don't mount the Docker socket. We learned about that. |
| Kernel exploit | Possible | We keep meaning to update the kernel |
| The intern | High | They don't have SSH access. Anymore. |

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/brightside/health-portal

# Definitely read the Dockerfile before running this
# (we'll wait)
# ...
# okay you didn't read it, did you

# Stand up the stack
docker compose up -d

# Verify it's running
curl http://127.0.0.1:3000

# If it's not running, check the logs
docker compose logs -f

# If the logs don't help, stare at the screen for 20 minutes
# then reboot
```

---

## 📋 Requirements

- Docker (recent enough that it has the security features we're using)
- Docker Compose (v2, because we use `docker compose` not `docker-compose`)
- A host with a kernel that hasn't been exploited yet
- nginx (configured correctly, unlike our first attempt)
- Faith

---

## ⚠️ Known Issues

- The `apt-get upgrade` line was commented out for a while. It is no longer commented out. We don't want to talk about it.
- The base image was previously unpinned. It is now pinned. We also don't want to talk about this.
- `WORKDIR app` (no leading slash) was a thing that happened. Briefly.
- We are aware that `172.30.30.0/24` may conflict with existing Docker networks on your host. This is your problem now.

---

## 🤝 Contributing

Please do not contribute vulnerabilities. We are working very hard to remove the ones we already have.

If you find a security issue, please disclose it responsibly by:
1. Opening a GitHub issue titled "URGENT"
2. Sending an email to security@brightside.example that nobody monitors
3. Tweeting at us
4. Giving up and just telling us in Slack

---

## 📜 License

This software is provided "as is", which in the medical data industry is a bold choice.

---

*BrightSide Health Portal — "Your data is probably safe with us."™*