# Pwnagotchi Lab

## Overview

This project documents my hands-on experience setting up, configuring, and experimenting with a Raspberry Pi-based Pwnagotchi device. Through this project, I gained practical experience with Linux commands, filesystem navigation, file permissions, SSH, SCP, and transferring files between Linux and Windows.

I also documented troubleshooting issues and explored how to manage network-capture files safely. This project helped me develop practical skills relevant to IT support, networking, Linux system administration, and cybersecurity.

## Project Objectives

- Explore how the Pwnagotchi hardware and software work together.
- Practice navigating the Linux filesystem and managing directories.
- Understand Linux file paths, permissions, and elevated privileges.
- Access a Linux device remotely using SSH.
- Transfer files securely between Linux and Windows using SCP.
- Troubleshoot command-line errors and document their causes.
- Learn about PCAP files and responsible handling of network data.
- Maintain technical documentation for my IT portfolio.

## Tools and Technologies

- Raspberry Pi-based Pwnagotchi hardware
- Pwnagotchi software
- Linux command line
- Windows 11 and Command Prompt
- SSH (Secure Shell)
- SCP (Secure Copy Protocol)
- Linux filesystem and permissions
- PCAP network-capture files
- GitHub and Markdown

## Work Completed

### 1. Accessed the Device Through SSH

Connected to the Pwnagotchi through an SSH terminal to interact with its Linux environment.

The terminal prompt appeared as:

`pi@sy10:~ $`

The device was reachable at `10.0.0.2` during the file-transfer process.

This gave me hands-on experience working with a remote Linux system through a command-line interface.

### 2. Inspected the Handshakes Directory

Created and inspected a directory named `handshakes` in the Pi user's home directory.

Command used:

```bash
ls -la ~/handshakes
```

The directory contained three existing PCAP files:

- `DADDYDAN_52bb9f9ed5b1.pcap`
- `PTOParadise_aaa7b9a571c8.pcap`
- `PTOParadiseGuest_aaa7b9a571c9.pcap`

The files had different sizes. Their presence confirmed that capture files existed, but further analysis would be needed to determine whether each contained a valid handshake.

### 3. Troubleshot Linux File Paths

While following a tutorial, I attempted to access files under:

`/root/handshakes/`

The command returned this error:

```text
cp: cannot stat '/root/handshakes/': No such file or directory
```

The error indicated that the specified source path could not be found.

My existing directory was located under the Pi user's home directory:

`/home/pi/handshakes/`

This helped me understand that `/root/` and `/home/pi/` refer to different locations. Using `sudo` provides elevated privileges, but it does not correct an invalid file path.

### 4. Investigated a Hostname-Resolution Warning

I also encountered the following warning:

```text
sudo: unable to resolve host sy10: Temporary failure in name resolution
```

This indicated a hostname-resolution problem separate from the directory-path error.

The warning was observed during a command attempt, but the underlying cause has not yet been confirmed. It is documented as a troubleshooting item for further investigation.

### 5. Transferred Files From Linux to Windows Using SCP

Used SCP to transfer the three PCAP files from the Pwnagotchi to a Windows destination folder.

**Source directory:**

`/home/pi/handshakes/`

**Intended Windows destination:**

`C:\Users\hypri\Downloads\pwnagotchi`

The terminal reported all three files reaching 100% during the transfer.

During troubleshooting, I initially attempted to use a Windows-style destination path from the Linux terminal. I learned that Windows commands and paths must be handled in the appropriate Windows environment, while Linux commands must be run in the Linux terminal.

The transfer demonstrated how SCP can be used to securely transfer files between systems. Destination-file verification remains a separate step.

## Troubleshooting Summary

| Issue | What I learned |
|---|---|
| Incorrect directory path | Verify the actual location of files before running copy commands. |
| Linux permissions | Elevated privileges do not make a nonexistent path valid. |
| Hostname-resolution warning | Investigate hostname configuration separately from filesystem errors. |
| Windows path used in Linux | Use commands and path formats appropriate to the current operating system. |
| SCP transfer reached 100% | Check the destination files to confirm the result. |

## Key Technical Lessons

- The `~` symbol refers to the current user's home directory.
- `/root/` is the root administrator's home directory and is separate from `/home/pi/`.
- `sudo` runs commands with elevated privileges.
- SSH provides remote command-line access to a system.
- SCP provides encrypted file transfer over SSH.
- Linux and Windows use different filesystem path formats and command environments.
- A completed transfer indicator does not replace destination verification.
- PCAP files may contain sensitive network information and should be handled responsibly.

## Security and Privacy

Network captures can contain information about devices, network activity, and communications. I will not publish raw PCAP files, credentials, private keys, or sensitive configuration data in this public repository.

Any further packet analysis will be performed only on systems and networks I own or have explicit authorization to assess. Screenshots and configuration examples will be reviewed and sanitized before publication.

## Project Outcome

I completed the hands-on Pwnagotchi setup and experimented with the device. I also practiced remote Linux access, inspected existing capture files, investigated filesystem errors, and performed an SCP transfer to Windows.

The project strengthened my understanding of Linux and Windows command-line environments, file paths, permissions, and secure file transfers.

## Further Validation and Documentation

Although the device setup and initial experimentation are complete, the following items remain for more thorough project documentation:

- [ ] Verify that all three transferred files exist in the Windows destination folder.
- [ ] Compare SHA-256 hashes to verify file integrity.
- [ ] Identify and document the exact Raspberry Pi hardware model.
- [ ] Record the installed Pwnagotchi software version.
- [ ] Investigate the hostname-resolution warning and document the verified cause.
- [ ] Add sanitized screenshots of the hardware, SSH session, troubleshooting, and transfer results.
- [ ] Document any authorized PCAP validation and analysis performed.

## Project Documentation

Screenshots, setup notes, troubleshooting records, and sanitized configuration examples will be organized in this repository as supporting evidence of the work completed.
