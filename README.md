# cisco

Great! With your answers available, I can guide you step by step from the beginning, including navigation in Packet Tracer and how to execute each command.

---

### Getting Started in Cisco Packet Tracer

1. **Launch Packet Tracer:**
   - Open Cisco Packet Tracer on your computer.

2. **Set up the topology:**
   - Drag and drop a switch from the "Network Devices" section in the left toolbar onto the workspace. 
   - Repeat for a second switch if you're working with S1 and S2.

3. **Access the Switch CLI:**
   - Double-click the switch (e.g., S1) on the workspace.
   - In the popup window, click the **CLI** tab.
   - Press **Enter** on your keyboard to activate the CLI.

---

### Part 1: Verify Default Switch Configuration

#### Step 1: Enter Privileged Mode
1. Type:
   ```bash
   enable
   ```
   - The prompt changes from `Switch>` to `Switch#`.

#### Step 2: Examine Configuration
1. Type the following to check the running configuration:
   ```bash
   show running-config
   ```
   - Count the **FastEthernet interfaces** (24) and **Gigabit Ethernet interfaces** (2).
   - Note the range of **vty lines** (0–15).

2. To check NVRAM (startup configuration), type:
   ```bash
   show startup-config
   ```
   - If the message `startup-config is not present` appears, it means no configuration has been saved yet.

---

### Part 2: Create a Basic Switch Configuration

#### Step 1: Assign a Name to the Switch
1. Enter global configuration mode:
   ```bash
   configure terminal
   ```
   - The prompt changes to `Switch(config)#`.

2. Assign a hostname:
   ```bash
   hostname S1
   ```
   - The prompt changes to `S1(config)#`.

3. Exit configuration mode:
   ```bash
   exit
   ```

#### Step 2: Secure Console Access
1. Re-enter global configuration mode:
   ```bash
   configure terminal
   ```

2. Access the console line:
   ```bash
   line console 0
   ```

3. Set a console password:
   ```bash
   password letmein
   ```

4. Enable password checking:
   ```bash
   login
   ```

5. Exit console configuration:
   ```bash
   exit
   ```

6. Exit global configuration mode:
   ```bash
   exit
   ```

#### Step 3: Verify Console Access
1. Exit the CLI completely:
   ```bash
   exit
   ```

2. Reconnect by pressing **Enter**. You will be prompted for a password.
   - Enter `letmein` to log in.

#### Step 4: Secure Privileged Mode Access
1. Enter privileged EXEC mode:
   ```bash
   enable
   ```

2. Enter global configuration mode:
   ```bash
   configure terminal
   ```

3. Set the enable password:
   ```bash
   enable password c1$c0
   ```

4. Exit configuration mode:
   ```bash
   exit
   ```

#### Step 5: Configure an Encrypted Password
1. Replace the enable password with a stronger encrypted password:
   ```bash
   configure terminal
   enable secret itsasecret
   exit
   ```

#### Step 6: Encrypt All Plain-Text Passwords
1. Enter global configuration mode again:
   ```bash
   configure terminal
   ```

2. Encrypt all plain-text passwords:
   ```bash
   service password-encryption
   exit
   ```

---

### Part 3: Configure a MOTD Banner

1. Enter global configuration mode:
   ```bash
   configure terminal
   ```

2. Create a message of the day banner:
   ```bash
   banner motd "This is a secure system. Authorized Access Only!"
   ```

3. Exit configuration mode:
   ```bash
   exit
   ```

---

### Part 4: Save Configuration to NVRAM

1. Save the running configuration:
   ```bash
   copy running-config startup-config
   ```
   - Press **Enter** when prompted for the destination filename.

2. Verify the saved configuration:
   ```bash
   show startup-config
   ```

---

### Part 5: Configure S2

For the second switch (S2), repeat the same steps as S1 with these differences:

1. **Hostname:** Use `S2` instead of `S1`:
   ```bash
   hostname S2
   ```

2. **Message of the Day:** Use this text instead:
   ```bash
   banner motd "Authorized access only. Unauthorized access is prohibited and violators will be prosecuted to the full extent of the law."
   ```

---

### Key Commands Recap
- `enable`: Enter privileged mode.
- `configure terminal`: Enter global configuration mode.
- `hostname <name>`: Set a hostname.
- `line console 0`: Configure console line settings.
- `password <password>`: Set a password for the console or vty line.
- `login`: Enable password checking.
- `enable password <password>`: Set a plaintext enable password.
- `enable secret <password>`: Set an encrypted enable password.
- `service password-encryption`: Encrypt all passwords.
- `banner motd "<message>"`: Set a message of the day.
- `copy running-config startup-config`: Save the configuration.

Let me know if you need further guidance!
