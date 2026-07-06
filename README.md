# School Hosting Project

Roadmap, documentation, and GitHub issue templates for hosting a school
website — including its MySQL database and SSL certificate — on a
DigitalOcean droplet.

This repository is used by Intellectitech interns on the Networking &
Cybersecurity track (Ntinda Hub) as part of the 8-week internship programme.

---

## What This Project Covers

- Provisioning and securing a DigitalOcean droplet (Ubuntu 22.04)
- Installing a LAMP stack (Apache, MySQL, PHP)
- Hosting a MySQL database for the school website
- Deploying the school website's files and connecting them to the database
- Pointing a domain name at the server (DNS)
- Installing a free SSL certificate with Let's Encrypt (Certbot)
- Final server hardening (firewall, Fail2Ban, automated backups)

---

## Repository Structure

```
school-hosting-project/
├── docs/      Step-by-step technical guides (Word documents)
├── issues/    Pre-written GitHub issue text for the project roadmap
└── README.md  This file
```

### docs/
Detailed, explained walkthroughs covering the full deployment process from
account creation through to a live HTTPS site — written for interns who are
doing this for the first time.

### issues/
Ready-to-paste GitHub issue titles and descriptions. Each issue includes a
task checklist and acceptance criteria, so progress can be tracked directly
in GitHub's Issues tab.

---

## Getting Started (For Interns)

1. Read through the guides in `docs/` in order.
2. Open the `issues/` folder and create each issue in this repository's
   **Issues** tab, in the order listed.
3. Work through each issue's checklist, ticking items off as you complete
   them.
4. Comment on each issue with screenshots/confirmation before closing it.
5. Do not skip ahead — later issues depend on earlier ones being finished
   (e.g. the database must exist before the website can be connected to it).

---

## Roadmap Order

1. Provision & secure the server
2. Install Apache, MySQL & PHP
3. Create & secure the database
4. Import the database schema
5. Deploy the website files
6. Connect the website to the database
7. Configure the Apache virtual host
8. Point the domain name (DNS)
9. Install SSL with Let's Encrypt
10. Confirm SSL auto-renewal
11. Final hardening (Fail2Ban + backups)
12. End-to-end verification & sign-off

---

## Maintained By

Intellectitech — Networking & Cybersecurity Track, Ntinda Hub
