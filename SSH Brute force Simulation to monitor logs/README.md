# SSH Brute Force Simulation & SOC Log Analysis

This project demonstrates a simulation of SSH brute-force attacks on two platforms—**Kali Linux** and **Android (Termux)**—and log analysis using Linux tools to mimic the role of a SOC analyst.

##  Objectives

- Simulate SSH brute-force attacks using Hydra.
- Deploy targets on Linux and Android (Termux).
- Monitor SSH logs using `journalctl`.
- Understand attacker tactics and SOC detection techniques.

##  Tools & Environment

- Kali Linux (for both attack and monitoring)
- Android Phone with Termux
- OpenSSH Server
- Hydra (brute-force tool)
- Custom password list (`password.txt`)
- Common Wi-Fi network for interaction

##  Step-by-Step Lab Summary

1. **Set up SSH on Kali & Android**
   - Installed OpenSSH and created a weak test user.
2. **Ran Hydra**
   - Brute-force command:  
     `hydra -l testuser -P password.txt ssh://127.0.0.1`
3. **Log Monitoring**
   - Real-time: `sudo journalctl -f | grep sshd`
   - Full history: `sudo journalctl -u ssh`

###  Applied Log Filters
```bash
# Successful logins:
sudo journalctl -u ssh | grep "Accepted password"

# Failed logins:
sudo journalctl -u ssh | grep "Failed password"

# Unique user attempts:
sudo journalctl -u ssh | grep "Accepted password" | awk '{print $9}' | sort | uniq -c | sort -nr

# Past 2 hours activity:
sudo journalctl -u ssh --since "2 hours ago"

# Additional filters:
sudo journalctl -u ssh | grep "Connection from"
sudo journalctl -u ssh | grep "Disconnected from"
sudo journalctl -u ssh | grep "Invalid user"
sudo journalctl -u ssh | grep "Accepted publickey"

```

4. **Android SSH (Termux) Test**
   - Opened SSH using sshd, then ran brute-force from Kali using Hydra.

## SOC Monitoring Insight
- Detected patterns in logs including repeated failures followed by a success.
- Demonstrated what SOC teams would flag as brute-force activity.

## Ethical Disclaimer
This simulation was conducted on personal devices in a controlled lab environment for educational purposes only.

## Cleanup
- Deleted test users and SSH files post-testing.
- Stopped SSH services.







