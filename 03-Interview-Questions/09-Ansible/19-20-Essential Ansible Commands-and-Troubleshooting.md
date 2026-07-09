# Essential Ansible Commands & Troubleshooting Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What is the purpose of the `ansible` command?

**Answer**

The `ansible` command is used to execute ad-hoc commands on one or more managed hosts without creating a playbook.

Example:

```bash
ansible all -m ping
```

**Explanation**

It is useful for quick administrative tasks, testing connectivity, gathering information, or executing a single module.

**Used in Production**

- Connectivity testing
- Restarting services
- Checking disk space
- Running shell commands
- Gathering facts

**Common Mistake**

Using ad-hoc commands for complex automation instead of creating reusable playbooks.

---

### Question 2

**Question**

What is the purpose of the `ansible-playbook` command?

**Answer**

The `ansible-playbook` command executes Ansible playbooks that automate multiple tasks across managed hosts.

Example:

```bash
ansible-playbook site.yml
```

**Explanation**

Unlike ad-hoc commands, playbooks provide reusable, version-controlled automation.

**Used in Production**

- Server provisioning
- Application deployment
- Configuration management
- Patch management

---

### Question 3

**Question**

What is the `ansible-inventory` command used for?

**Answer**

The `ansible-inventory` command displays and validates inventory information.

Example:

```bash
ansible-inventory --list
```

**Explanation**

It helps verify that hosts, groups, and variables are loaded correctly before running automation.

**Used in Production**

- Inventory validation
- Troubleshooting inventory issues
- Verifying dynamic inventory output

---

### Question 4

**Question**

What is the purpose of the `ansible-galaxy` command?

**Answer**

`ansible-galaxy` installs, manages, and creates Ansible Roles and Collections.

Example:

```bash
ansible-galaxy install geerlingguy.nginx
```

**Explanation**

It allows engineers to reuse community-maintained automation instead of writing everything from scratch.

**Used in Production**

Installing reusable roles for web servers, databases, Docker, Kubernetes, and monitoring tools.

---

### Question 5

**Question**

What is the `ansible-vault` command used for?

**Answer**

`ansible-vault` encrypts and decrypts sensitive files such as passwords and API keys.

Examples:

```bash
ansible-vault create secrets.yml
```

```bash
ansible-vault encrypt secrets.yml
```

**Explanation**

Vault protects confidential information stored in playbooks or variable files.

**Used in Production**

- Database passwords
- Cloud credentials
- SSH keys
- API tokens

---

### Question 6

**Question**

What is the purpose of the `ansible-doc` command?

**Answer**

`ansible-doc` displays documentation for Ansible modules.

Example:

```bash
ansible-doc copy
```

**Explanation**

It provides module descriptions, parameters, return values, and usage examples directly from the command line.

**Used in Production**

Quickly learning module syntax without searching online.

---

### Question 7

**Question**

What are the most common causes of inventory issues in Ansible?

**Answer**

Common causes include:

- Incorrect hostnames
- Wrong IP addresses
- Invalid group names
- Inventory file syntax errors
- Incorrect inventory path

**Explanation**

If Ansible cannot locate or interpret hosts correctly, playbook execution may fail before any tasks are run.

**Common Mistake**

Forgetting to specify the correct inventory file using `-i`.

---

### Question 8

**Question**

What causes SSH connection failures in Ansible?

**Answer**

Common causes include:

- SSH service not running
- Incorrect username
- Wrong SSH key
- Firewall blocking port 22
- Network connectivity issues

**Explanation**

Ansible relies on SSH for communication with Linux managed nodes.

**Used in Production**

Troubleshooting deployment failures across Linux servers.

---

### Question 9

**Question**

What are common authentication errors in Ansible?

**Answer**

Examples include:

- Incorrect SSH credentials
- Invalid SSH keys
- Incorrect sudo password
- Missing `become` privileges
- Cloud authentication failures

**Explanation**

Authentication must succeed before Ansible can execute any tasks.

**Common Mistake**

Assuming network issues when the actual problem is incorrect credentials.

---

### Question 10

**Question**

What are YAML syntax errors, and why do they occur?

**Answer**

YAML syntax errors occur due to formatting mistakes such as:

- Incorrect indentation
- Missing colons
- Improper spacing
- Invalid list formatting

**Explanation**

YAML is indentation-sensitive. Even small formatting mistakes can prevent playbooks from running.

**Used in Production**

All Ansible playbooks, inventory files, and variable files use YAML syntax.

---

### Question 11

**Question**

What causes module failures in Ansible?

**Answer**

Common causes include:

- Invalid parameters
- Missing dependencies
- Unsupported operating system
- Permission issues
- Incorrect module usage

**Explanation**

Modules expect specific parameters and operating environments. Incorrect inputs or missing prerequisites often result in failures.

**Used in Production**

Troubleshooting failed package installations, service management, and cloud provisioning.

---

### Question 12

**Question**

How do you troubleshoot playbook execution failures?

**Answer**

A systematic approach includes:

1. Check YAML syntax
2. Verify inventory
3. Test SSH connectivity
4. Validate credentials
5. Review module parameters
6. Examine task output
7. Increase verbosity using:

```bash
ansible-playbook site.yml -vvv
```

**Explanation**

Following a structured troubleshooting process helps isolate the root cause efficiently.

**Common Mistake**

Changing multiple things at once instead of identifying the actual failure.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your playbook reports "No hosts matched." What would you check first?

**Answer**

Verify the inventory file, host names, group names, and ensure the correct inventory is specified using the `-i` option.

**Explanation**

This error usually indicates that Ansible cannot match the target hosts defined in the playbook with those in the inventory.

---

### Scenario 2

**Question**

The command `ansible all -m ping` returns "UNREACHABLE." How would you troubleshoot the issue?

**Answer**

Check:

- Network connectivity
- SSH service status
- Firewall rules
- SSH credentials
- Inventory configuration
- Host reachability

**Explanation**

Most "UNREACHABLE" errors are caused by connectivity or authentication issues rather than Ansible itself.

---

### Scenario 3

**Question**

A playbook fails with "Permission denied (publickey)." What is the likely cause?

**Answer**

The SSH key is missing, incorrect, or not authorized on the target server.

**Explanation**

Verify that the correct private key is being used and the corresponding public key exists in the server's `authorized_keys` file.

---

### Scenario 4

**Question**

A playbook fails with a YAML parsing error. What would you do?

**Answer**

Check the file for indentation errors, missing colons, incorrect spacing, or malformed lists. Validate the syntax using a YAML linter if available.

**Explanation**

YAML formatting errors are among the most common causes of playbook failures.

---

### Scenario 5

**Question**

A package installation task fails because the package name is invalid. How would you identify the issue?

**Answer**

Review the task output, verify the package name for the target operating system, and consult the module documentation using `ansible-doc`.

**Explanation**

Different Linux distributions often use different package names.

---

### Scenario 6

**Question**

Your playbook works on Ubuntu but fails on Red Hat Enterprise Linux. What is the likely cause?

**Answer**

The playbook may use Ubuntu-specific modules, package names, or service names.

**Explanation**

Use Ansible Facts and conditional tasks to support multiple operating systems.

---

### Scenario 7

**Question**

An encrypted Vault file causes the playbook to fail with a decryption error. What would you check?

**Answer**

Verify that the correct Vault password or Vault password file is being supplied during playbook execution.

**Explanation**

Without the correct password, Ansible cannot decrypt encrypted variables.

---

### Scenario 8

**Question**

A Jenkins pipeline successfully starts an Ansible playbook, but every task fails due to authentication errors. What would you investigate?

**Answer**

Verify the Jenkins credentials, SSH keys, inventory configuration, and any required `become` credentials.

**Explanation**

The pipeline may not have access to the same authentication information available during manual execution.

---

### Scenario 9

**Question**

A teammate is unsure how to use the `template` module. Instead of searching the internet, which command would you recommend?

**Answer**

Use:

```bash
ansible-doc template
```

**Explanation**

The command provides official documentation, supported parameters, and usage examples directly from the installed Ansible version.

---

### Scenario 10

**Question**

Your production deployment fails during playbook execution, but the error message is unclear. How would you gather more information?

**Answer**

Re-run the playbook with increased verbosity:

```bash
ansible-playbook site.yml -vvv
```

or

```bash
ansible-playbook site.yml -vvvv
```

**Explanation**

Verbose output provides detailed execution logs, SSH communication details, and module responses, making it easier to identify the root cause of the failure.
