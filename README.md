# osTicket Help Desk Lab – Integrated with Active Directory (JS3homelab)

## Overview
This project documents the deployment and operation of an **osTicket help desk system** integrated with a Windows Server Active Directory lab (Domain: JS3homelab).

The purpose of this lab is to simulate real-world IT support workflows, where help desk tickets are created by domain users and resolved through administrative actions in Active Directory.

This project focuses on:
- Ticket lifecycle management
- Account lockout troubleshooting
- Password resets
- User verification
- Documentation of resolution steps
- Cross-system troubleshooting (osTicket + AD + client machine)

---

## Lab Environment

### Infrastructure
- **Virtualization Platform:** Proxmox VE
- **Domain Controller:** Windows Server (Domain: JS3homelab)
- **Client Machine:** Windows 10 Pro (Domain-joined)
- **Ticketing System:** osTicket (VM)
- **Network:** VLAN-segmented homelab (VLAN 40 – Homelab/Servers)

### Domain Information
- Domain Name: JS3homelab.local
- Test User: testuser1
- IT Admin Account: Domain Administrator

---

## Architecture Overview
- **Domain user (windows 10 pro client)
- **Login issue / Account Lockout
- **OsTicket (web portal)
- **Technician Assigned
- **Active Directory (Windows Sever DC)
- **Account Unlock / Password Resest
- ** User Login Retest (Client Machine)


The workflow mirrors real-world IT support processes in school or enterprise environments.

---

# Scenario-Based Ticket Simulation

Each scenario represents a realistic IT support request tied directly to Active Directory actions.

---

## Scenario 1 – Account Lockout & Password Reset

### Ticket Simulation
User reports:
> “I can’t log into my computer. It says my account is locked.”

---

### Step 1 – Trigger Account Lockout
- On Windows 10 client, intentionally enter incorrect password multiple times.
- Confirm account lockout message.

📸 **Screenshot Location (Client Machine):**
- Windows login screen showing account lockout message

---

### Step 2 – Ticket Creation in osTicket
- Log into osTicket as test user (or simulate submission)
- Create ticket:
  - Category: Account Access
  - Description: User locked out after failed login attempts

📸 **Screenshot Locations (osTicket):**
- New ticket submission screen
- Ticket overview dashboard showing open ticket
- Ticket details page

---

### Step 3 – Active Directory Resolution
- Log into Domain Controller
- Open Active Directory Users and Computers (ADUC)
- Locate testuser1
- Confirm account is locked
- Unlock account
- Reset password
- Enable "User must change password at next logon"

📸 **Screenshot Locations (Domain Controller):**
- ADUC showing locked account
- Account properties → Unlock checkbox
- Password reset dialog

---

### Step 4 – Validate on Client Machine
- Return to Windows 10 client
- Log in using new password
- Change password at prompt

📸 **Screenshot Locations (Client Machine):**
- Successful login screen
- Password change prompt

---

### Step 5 – Ticket Resolution Documentation
- Return to osTicket
- Add internal note documenting:
  - Account was locked due to failed attempts
  - Password reset performed
  - User instructed to change password
- Mark ticket as Resolved

📸 **Screenshot Locations (osTicket):**
- Technician response
- Ticket marked closed
- Ticket status dashboard

---

## Scenario 2 – Disabled Account (Employee Termination Simulation)

### Ticket Simulation
> “User cannot log in — account appears disabled.”

### Steps
1. Disable user account in ADUC
2. Attempt login on client (should fail)
3. Create ticket in osTicket
4. Re-enable account in AD
5. Verify login
6. Close ticket with documentation

📸 Capture:
- Disabled account in ADUC
- Login failure
- Ticket lifecycle progression

---

## Scenario 3 – Network Drive Not Mapping

### Ticket Simulation
> “My shared drive isn’t showing up after login.”

### Steps
1. Verify share permissions on server
2. Check group membership in AD
3. Run `gpupdate /force` on client
4. Confirm drive mapping restored
5. Document resolution in ticket

📸 Capture:
- Share permissions
- Group membership
- Client drive mapping
- Ticket resolution notes

---

# Ticket Lifecycle Demonstrated

1. Ticket creation
2. Technician assignment
3. AD verification
4. Administrative fix
5. Validation on client
6. Resolution documentation
7. Ticket closure

This reflects real-world help desk workflow and accountability.

---

# Cross-System Troubleshooting Skills Demonstrated

- Understanding AD authentication flow
- Account lockout thresholds
- Password policy enforcement
- User verification procedures
- Ticket documentation best practices
- Client-side validation
- Administrative privilege usage

---

# Validation & Testing Artifacts

Include screenshots of:

## osTicket
- Agent dashboard
- Ticket queue
- Ticket detail view
- Internal notes section
- Closed ticket confirmation

## Active Directory (Domain Controller)
- ADUC user properties
- Locked vs unlocked account
- Password reset dialog
- Disabled account checkbox

## Windows 10 Client
- Account lockout message
- Login success after reset
- Domain login screen

---

# Future Enhancements

- LDAP authentication integration for osTicket agents
- Automatic ticket generation from security alerts (Wazuh integration)
- Email-based ticket intake
- Role-based technician permissions via AD security groups
- Ticket reporting dashboard

---

# Why This Project Matters

This lab demonstrates practical experience with:

- Identity management
- Help desk ticket workflows
- Real-world IT troubleshooting
- Documentation and accountability
- Cross-platform system integration

It reflects responsibilities commonly required in:
- School district IT support
- MSP help desk roles
- Entry-level systems administration

---

# Resume / LinkedIn Summary

Deployed and documented an osTicket help desk system integrated with a Windows Active Directory domain to simulate real-world IT support workflows including account lockout resolution, password resets, and ticket lifecycle management.
