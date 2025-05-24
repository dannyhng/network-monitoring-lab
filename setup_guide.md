# Setup Guide: Network Monitoring with Nagios

This guide explains how I set up Nagios Core on an Ubuntu virtual machine to monitor multiple test servers.

## 1. Install Nagios

```bash
sudo apt update
sudo apt install nagios4 nagios-plugins-contrib nagios-nrpe-plugin
```

## 2. Configure Hosts
Edit the host configuration:

```bash
sudo nano /etc/nagios4/conf.d/hosts.cfg
```

Example:

```bash
define host {
  use             generic-host
  host_name       test-server-1
  address         192.168.1.100
}
```

## 3. Add Services to Monitor

Edit:

```bash
sudo nano /etc/nagios4/conf.d/services.cfg
```

Example:

```bash
define service {
  use                 generic-service
  host_name           test-server-1
  service_description CPU Load
  check_command       check_load
}
```

## 4. Restart Nagios

```bash
sudo systemctl restart nagios4
```

Access the web dashboard at:

```bash
http://your-server-ip/nagios4
```

## 5. Simulate Alerts

Temporarily increase CPU load or stop services to trigger alerts.

## 6. Document Incidents

Use incident_log_template.md to log alert response.

