# Initial Windows Server Setup and Installing Active Directory Domain Services

## Description

This project documents my initial Windows Server installation and the steps I took to install and configure Active Directory Domain Services (AD DS), including promoting the server to a domain controller.

## Languages and Tools Utilized

- Active Directory
- CMD

## Environments

- VMware Workstation Pro
- Windows Server 2025

## Links

- VMware Workstation Pro 25H2: [Download here](https://support.broadcom.com/group/ecx/productfiles)
- Windows Server 2025 ISO (64-bit): [Download here](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2025)

## Program Walkthrough

Diagram showing what I'll be doing in this first lab:

*(insert architecture/flow diagram here)*

---

## Step 1: Rename the Server

I started by renaming the server to something clear, since the default name is usually random and meaningless (e.g. `WIN-K3J9XYZ`), whereas a name like `FileServer01` instantly tells you its function. It's important to do this **before** promoting the server to a domain controller, since renaming it afterward is a much bigger headache.

<img width="318" height="185" alt="Rename server" src="https://github.com/user-attachments/assets/cd6730ea-109b-4152-9ab7-d314a90d34db" />

> You must restart the VM for the rename to take effect.

To confirm the change took effect, open Command Prompt (type `cmd` in the search bar) and run:

```cmd
hostname
```

It should return `FileServer01`.

<img width="447" height="150" alt="Hostname confirmation" src="https://github.com/user-attachments/assets/e7799a60-21f2-4a6f-804d-828a6472aeac" />

---

## Step 2: Configure Windows Updates

Before doing anything else, it's important to fully patch the server so it's stable and secure. Updates often require multiple reboots, so you don't want one interrupting you mid-way through configuring the domain.

Go to **Settings > Windows Update** and make sure the server is fully up to date.

<img width="703" height="165" alt="Windows Update" src="https://github.com/user-attachments/assets/ba423400-eda3-4f59-ac6e-8b5a15b8b12f" />

---

## Step 3: Enable Remote Management

Remote management is important for servers so you can manage them without logging in directly — you can administer the server from any computer on the network. This also mirrors real-world practice.

To enable it, open **Server Manager**, click **Local Server** in the left-hand pane, and confirm Remote Management is enabled. If it isn't, click the setting and enable it.

<img width="226" height="16" alt="Remote management enabled" src="https://github.com/user-attachments/assets/dabfa4c7-9f5a-4582-b1f5-09ca618927d5" />

---

## Step 4: Install Active Directory Domain Services

Open **Server Manager**, click **Add roles and features** in the top right, and click **Next** until you reach **Server Roles**. Check **Active Directory Domain Services**.

<img width="780" height="548" alt="Add AD DS role" src="https://github.com/user-attachments/assets/10752681-5524-4783-8b33-c800f82f8713" />

Click **Next** until you reach **Install**.

> Don't close the wizard once installation finishes — the next step (promoting the server to a domain controller) follows immediately from this window.

---

## Step 5: Promote the Server to a Domain Controller

Once installation completes, click **Promote this server to a domain controller**.

<img width="781" height="547" alt="Promote to domain controller" src="https://github.com/user-attachments/assets/5e771429-6a35-4861-920a-44fdb47775a0" />

In the new window, select **Add a new forest** and enter a domain name. Since this is a home lab, avoid using a real domain name — something like `homelab.local` works well.

> Double-check your spelling here. A small typo (e.g. `.lcoal` instead of `.local`) can be a real pain to fix later.

<img width="757" height="547" alt="New forest domain name" src="https://github.com/user-attachments/assets/285273d9-e4eb-4fd8-9710-81ea8749ff9d" />

Confirm **Windows Server 2025** is selected as the forest/domain functional level.

<img width="756" height="545" alt="Functional level selection" src="https://github.com/user-attachments/assets/eb590cff-a61f-47ee-94aa-4c75aa25b798" />

Choose a Directory Services Restore Mode (DSRM) password and store it somewhere safe — don't rely on memory alone.

Click **Next** through the remaining screens until **Review Options**, and take a moment to confirm everything — especially the domain name — is correct.

All prerequisite checks should pass:

<img width="727" height="33" alt="Prerequisites check passed" src="https://github.com/user-attachments/assets/82d7731f-fddf-478e-8504-f37e02be9561" />

> If you see an error here, go back a step and forward again — sometimes the prerequisite checks just need a second pass to clear.

You'll then see a sign-out notice. Click **Close**.

<img width="598" height="194" alt="Sign out notice" src="https://github.com/user-attachments/assets/3432073e-2504-4f7f-a260-af1ebcddf15a" />

---

## Step 6: Confirm Promotion

After the server reboots, it should now show as a domain controller, with the domain name visible in Server Manager.

<img width="660" height="442" alt="Domain controller confirmed" src="https://github.com/user-attachments/assets/4eb908a4-e306-45c9-af59-91152d240bee" />

 
