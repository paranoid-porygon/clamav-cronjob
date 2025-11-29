clamav-cronjob
============

ClamAV is an open source (GPL) antivirus engine designed for detecting Trojans, viruses, malware and other malicious threats.

Rkhunter (Rootkit Hunter) is a Unix-based tool that scans for rootkits, backdoors and possible local exploits.

The script scans pre-defined system locations depending on the day of the week and sends an email notification with a ClamAV or rkhunter log attached if any malware has been found.

# Installation on Debian/Ubuntu

The following packages are used by the script:
 
* ClamAV
* inetutils
* man-pages
* Rkhunter
 
To install:

```
$ sudo pacman -S clamav rkhunter git inetutils man-pages
$ git clone https://github.com/paranoid-porygon/clamav-cronjob.git
$ chmod u+x ./clamav-cronjob/*.sh
$ sudo ./clamav-cronjob/clamav-rkhunter-scan.sh
```

# Configuration

For systems that are up 24/7, you may want to put the script in the directory <code>/etc/cron.daily/</code> for daily execution.

# Log Rotation

Log rotation is not handled by the script, however, you can use logrotate to achieve that if required.

Simply add your log rotation config to `/etc/logrotate.d/clamav-daily` and you should be good to go, e.g.:

```
/var/log/clamav/*.log {
  daily
  rotate 0
}
```

When rotate count is set to 0, old versions are removed rather than rotated.
