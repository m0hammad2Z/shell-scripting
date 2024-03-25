# Shell Scripting Project

## Introduction

This project includes two shell scripts developed for Linux system administration: a backup script and a system health check script. These scripts aim to automate common tasks and enhance efficiency.

## Backup Script

The backup script automates the process of backing up user-specified directories.

### Features

* **Backup Options:**
    * `-o <output directory>`: Specify the output directory for the backup.
    * `-z <compression type>`: Specify the compression type (gz, bz2, xz).
    * `-e`: Enable encryption with passphrase input.
    * `-k <encryption key>`: Specify encryption key (used with `-e`).
    * `-r`: Remove the directory after backup.
    * `-c`: Just copy the directory without compression.
    * `-p <number of cores>`: Specify the number of CPU cores to use.
    * `-l <log file>`: Specify the log file.
    * `-h`: Display help.
* **Log Handling:** Logs messages with timestamps are recorded in a specified log file (default: `/var/log/backup.log`).
* **Parallel Backup:** The script supports parallel execution to speed up the backup process.
* **Compression and Encryption:** Users can choose from three compression types and optionally encrypt backups using GPG for enhanced security.
* **Directory Removal and Just Copy:** Users can choose to remove the original directory after a successful backup (`-r`). The `-c` option enables copying without compression.
* **Output and Results:** After completion, the script provides a summary of successful and failed backups along with their sizes.

### Optimizations and Impact

* **Parallelization:** The backup script utilizes parallel execution to backup multiple directories simultaneously, reducing backup time, especially for multiple directories.
* **Dynamic Log Handling:** The script allows users to specify a custom log file using the `-l` option. If no file is specified, the default is set to `/var/log/backup.log`. This enhances flexibility and readability.
* **Improved Error Handling:** The script catches errors during execution and records them in a temporary error file. After completion, it checks for errors and prints them to the console, improving visibility of potential issues during backup operations. Users are immediately notified of errors, allowing for quick troubleshooting and resolution.

## System Health Check Script

The system health check script evaluates various aspects of system health, including CPU usage, memory status, disk usage, running services, and the latest system update.

### Features

* **Options:**
    * `-a`: Perform all health checks.
    * `-c`: Check memory usage.
    * `-m`: Check memory usage (alias for `-c`).
    * `-d`: Check disk usage.
    * `-r`: Check running services.
    * `-u`: Check last system update.
    * `-l <log file>`: Specify the log file.
* **Health Report:** The script generates a detailed report (`syshealth_<timestamp>.txt`) containing information about general system details, CPU usage, memory status, top processes consuming resources, disk information, running services, and the last update.
* **Recommendations:** The script provides recommendations and warnings based on observed system values. For example, it warns about high CPU usage and recommends actions to optimize system performance.

### Optimizations and Impact

* **CPU, Disk, and Memory Usage Warnings:** The script checks for high CPU, memory, and disk usage. If usage exceeds a specified threshold, the script warns the user with recommendations. This provides early notice for investigation and optimization.
* **Detailed Health Report:** The script offers a comprehensive report, which is a key feature. Users gain a consolidated and detailed overview of the system's health, simplifying the identification and resolution of potential issues.

## Scheduled Tasks

Task scheduling is crucial in system administration, ensuring critical processes run at the desired time without manual intervention.

* **Automating the Backup Script:** Regular backups can be automated by integrating the backup script into scheduled tasks. This ensures essential data is consistently backed up at specified intervals, providing data protection.

  ## Conclusion

Shell scripts offer powerful solutions for automating backup and system health operations on Linux systems. They provide flexibility, configurability, and performance improvements.

## Note
Some commands in the scripts require administrative privileges. The backup task should be edited in the

## License
MIT License [Link to MIT License](https://opensource.org/licenses/MIT)

