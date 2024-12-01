
## Systemd Overview 
**Systemd**  is a system and service manager for Linux operating systems, designed to be the first process started by the kernel and to manage system processes and services throughout the system's lifecycle. It aims to provide better management and performance of services and dependencies.

### Key Concepts: 
 
- **Units** : Basic objects that systemd manages, described by unit files. 
  - **Services (`.service`)** : Define how to start, stop, reload, and manage daemons or background services.
 
  - **Sockets (`.socket`)** : Define network or IPC sockets that systemd should manage, often paired with service units to activate on-demand.
 
  - **Targets (`.target`)** : Group units and define synchronization points during system boot or shutdown (similar to runlevels).

### Systemd Cheatsheet 

#### Managing Services 
 
- **Start a service:** 

```sh
systemctl start <service-name>
```
 
- **Stop a service:** 

```sh
systemctl stop <service-name>
```
 
- **Restart a service:** 

```sh
systemctl restart <service-name>
```
 
- **Reload a service's configuration without restarting:** 

```sh
systemctl reload <service-name>
```
 
- **Enable a service to start on boot:** 

```sh
systemctl enable <service-name>
```
 
- **Disable a service from starting on boot:** 

```sh
systemctl disable <service-name>
```
 
- **Check the status of a service:** 

```sh
systemctl status <service-name>
```
 
- **List all active services:** 

```sh
systemctl list-units --type=service --state=active
```

#### Managing Sockets 
 
- **Start a socket:** 

```sh
systemctl start <socket-name>
```
 
- **Stop a socket:** 

```sh
systemctl stop <socket-name>
```
 
- **Enable a socket to start on boot:** 

```sh
systemctl enable <socket-name>
```
 
- **Disable a socket from starting on boot:** 

```sh
systemctl disable <socket-name>
```
 
- **Check the status of a socket:** 

```sh
systemctl status <socket-name>
```

#### Managing Targets 
 
- **Change to a different target (e.g., multi-user.target):** 

```sh
systemctl isolate <target-name>
```
 
- **Set default target:** 

```sh
systemctl set-default <target-name>
```
 
- **Get default target:** 

```sh
systemctl get-default
```

### Journalctl Cheatsheet 

#### Viewing Logs 
 
- **View all logs:** 

```sh
journalctl
```
 
- **View logs for a specific service:** 

```sh
journalctl -u <service-name>
```
 
- **View logs for the current boot:** 

```sh
journalctl -b
```
 
- **View logs for a previous boot:** 

```sh
journalctl -b -1
```
 
- **Follow logs in real-time (similar to `tail -f`):** 

```sh
journalctl -f
```
 
- **View logs within a specific time range:** 

```sh
journalctl --since "2024-07-10 10:00:00" --until "2024-07-10 12:00:00"
```
 
- **View the last 100 lines of logs:** 

```sh
journalctl -n 100
```


**Some tweaks to improve performance**

In /etc/systemd/system.conf

DefaultTimeoutStartSec=15s
DefaultTimeoutStopSec=10s
DefaultTimeoutAbortSec=11s
DefaultDeviceTimeoutSec=15s

### Summary 
**Systemd**  is a comprehensive and powerful system and service manager that brings consistency and control over services, processes, and the overall system lifecycle in Linux. Its command-line utilities like `systemctl` for service management and `journalctl` for log management are essential tools for system administrators.