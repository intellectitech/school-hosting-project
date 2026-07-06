# Project 1 — Provision & Secure the Server
### Copy-paste ready for the organisation repository (GitHub Issues)

Copy the **Title** into GitHub's title field, and everything under **Description** into the issue body. This is the first project in the roadmap — nothing else (database, website, SSL) can start until this one is fully checked off.

---

**Title:**
```
Project 1: Provision and Secure the DigitalOcean Server for the School Website
```

**Labels:** `infrastructure`, `security`, `project-1`

**Assignee:** _(assign the intern responsible)_

**Description:**
```
## Overview

This is Project 1 of the School Website Hosting roadmap. Before we can install
any software, host a database, or deploy the website, we need a cloud server
that is running, reachable, and locked down against attackers.

By the end of this project, an intern should have a live DigitalOcean droplet
that they can log into securely, with root login and password login disabled,
and a firewall allowing only the traffic the project actually needs.

## Goal

A single Ubuntu 22.04 droplet, fully hardened, ready for Project 2 (installing
Apache, MySQL, and PHP) to begin.

---

## Detailed To-Do List

### Part A — DigitalOcean Account
- [ ] Create a DigitalOcean account (or confirm access to the shared
      organisation account, if one is provided)
- [ ] Verify the account's email address
- [ ] Confirm a billing method is on file (card or education credit)
- [ ] Create a Project inside DigitalOcean called `school-website` to keep
      resources organised

### Part B — SSH Key Setup (on your own laptop)
- [ ] Generate an SSH key pair:
      `ssh-keygen -t ed25519 -C "your-name@intellectitech"`
- [ ] Confirm two files now exist in `~/.ssh`: `id_ed25519` (private — never
      share) and `id_ed25519.pub` (public — safe to share)
- [ ] Print and copy the public key:
      `cat ~/.ssh/id_ed25519.pub`

### Part C — Create the Droplet
- [ ] In the DigitalOcean dashboard, click **Create → Droplets**
- [ ] Choose image: **Ubuntu 22.04 (LTS) x64**
- [ ] Choose plan: **Basic → Regular SSD**, smallest size (~1 GB RAM / 1 vCPU)
- [ ] Choose the datacenter region closest to our users
- [ ] Under Authentication, choose **SSH Key** (not Password) and paste the
      public key copied in Part B
- [ ] Set the hostname to something clear, e.g. `school-web01`
- [ ] Assign the droplet to the `school-website` project
- [ ] Click **Create Droplet** and wait for it to become **Active**
- [ ] Record the droplet's public IPv4 address as a comment on this issue

### Part D — First Login and System Update
- [ ] Log in for the first time: `ssh root@YOUR_DROPLET_IP`
- [ ] Update all installed software:
      `apt update && apt upgrade -y`

### Part E — Create a Non-Root Admin User
- [ ] Create a new user: `adduser schooladmin`
- [ ] Add it to the sudo group: `usermod -aG sudo schooladmin`
- [ ] Copy your SSH key to the new user:
      `rsync --archive --chown=schooladmin:schooladmin ~/.ssh /home/schooladmin`
- [ ] **In a second, separate terminal window** (keep the root session open),
      confirm you can log in as the new user with no password prompt:
      `ssh schooladmin@YOUR_DROPLET_IP`

### Part F — Lock Down SSH Access
- [ ] Only after Part E is confirmed working, edit the SSH config on the
      server: `nano /etc/ssh/sshd_config`
- [ ] Set `PermitRootLogin no`
- [ ] Set `PasswordAuthentication no`
- [ ] Restart SSH: `systemctl restart ssh`
- [ ] Confirm root login is now refused, and password login no longer works
      anywhere on the server

### Part G — Configure the Firewall
- [ ] From now on, always work as `schooladmin` using `sudo`
- [ ] Allow SSH: `sudo ufw allow OpenSSH`
- [ ] Allow HTTP: `sudo ufw allow 80/tcp`
- [ ] Allow HTTPS: `sudo ufw allow 443/tcp`
- [ ] Enable the firewall: `sudo ufw enable`
- [ ] Confirm status: `sudo ufw status verbose`

### Part H — Final Checks
- [ ] Confirm no other ports are open besides 22, 80, and 443
- [ ] Confirm the droplet's IP address, `schooladmin` username, and SSH key
      location are recorded somewhere the whole team can find (e.g. this issue,
      or the team's shared notes doc)
- [ ] Take a screenshot of `sudo ufw status verbose` and attach it to this issue

---

## Acceptance Criteria

- [ ] Droplet is Active in DigitalOcean, running Ubuntu 22.04
- [ ] `ssh schooladmin@YOUR_DROPLET_IP` logs in with an SSH key, no password
      prompt
- [ ] Attempting `ssh root@YOUR_DROPLET_IP` is refused
- [ ] `sudo ufw status verbose` shows exactly OpenSSH, 80/tcp, and 443/tcp
      allowed — nothing else
- [ ] Droplet IP address and admin username are documented on this issue

## Definition of Done

This project is complete when every checkbox above is ticked, the screenshot
is attached, and a trainer/lead has reviewed and approved this issue.

## Blocks

This project blocks **Project 2 — Install Apache, MySQL & PHP**, which cannot
start until this server exists and is confirmed secure.
```
