# Variables & Modules Interview Questions

## Most Frequently Asked Interview Questions

### Question 1

**Question**

What are Variables in Ansible, and why are they important?

**Answer**

Variables are reusable values used to make playbooks dynamic, flexible, and easier to maintain.

Example:

```yaml
vars:
  package_name: nginx
```

Usage:

```yaml
name: "{{ package_name }}"
```

**Explanation**

Instead of hardcoding values, variables allow the same playbook to work across different environments by simply changing variable values.

**Used in Production**

- Package names
- Ports
- File paths
- Usernames
- Environment-specific configurations

**Common Mistake**

Many candidates hardcode values instead of using variables, making playbooks difficult to reuse.

---

### Question 2

**Question**

What are the different types of Variables in Ansible?

**Answer**

Common variable types include:

- Playbook Variables (`vars`)
- Inventory Variables
- Host Variables
- Group Variables
- Extra Variables (`--extra-vars`)
- Registered Variables
- Facts

**Explanation**

Variables can be defined at different levels depending on the scope and use case.

**Used in Production**

Organizations use inventory variables for infrastructure settings and playbook variables for application-specific configurations.

---

### Question 3

**Question**

What is Variable Precedence in Ansible?

**Answer**

Variable precedence determines which variable value Ansible uses when the same variable is defined in multiple places.

Generally, higher-precedence variables override lower-precedence ones.

Example (highest priority):

1. Extra Variables (`--extra-vars`)
2. Task Variables
3. Play Variables
4. Host Variables
5. Group Variables
6. Inventory Variables

**Explanation**

Understanding precedence helps avoid unexpected configuration behavior.

**Used in Production**

Useful when different environments require different values without modifying playbooks.

**Common Mistake**

Candidates often assume Ansible merges variable values automatically. In most cases, higher-precedence values replace lower-precedence ones.

---

### Question 4

**Question**

What are Registered Variables in Ansible?

**Answer**

Registered Variables store the output of a task so it can be used later in the playbook.

Example:

```yaml
- name: Check uptime
  command: uptime
  register: uptime_output
```

**Explanation**

The output becomes available as a variable and can be referenced in later tasks.

**Used in Production**

- Checking command results
- Conditional execution
- Parsing command output

---

### Question 5

**Question**

What are Facts in Ansible?

**Answer**

Facts are automatically collected system information about managed nodes.

Example facts include:

- Operating System
- IP Address
- Hostname
- CPU
- Memory
- Disk Information

**Explanation**

Facts are gathered using the `setup` module before playbook execution unless fact gathering is disabled.

**Used in Production**

Playbooks often use facts to apply different configurations based on the operating system or hardware.

**Common Mistake**

Some candidates think facts must always be manually defined. They are automatically collected by default.

---

### Question 6

**Question**

What are Modules in Ansible?

**Answer**

Modules are reusable units of work that perform specific automation tasks.

Examples:

- copy
- file
- service
- package
- user
- git

**Explanation**

Every Ansible task executes a module on the managed node.

**Used in Production**

Modules automate nearly every administrative task performed by DevOps engineers.

---

### Question 7

**Question**

What is the difference between the `command` and `shell` modules?

**Answer**

The `command` module executes commands directly without invoking a shell.

The `shell` module executes commands through the system shell and supports shell features.

Example:

```yaml
command: ls
```

Example:

```yaml
shell: cat file.txt | grep nginx
```

**Explanation**

Use the `command` module whenever possible because it is more secure. Use the `shell` module only when shell functionality such as pipes, redirection, or environment variables is required.

**Used in Production**

- `command` for simple commands
- `shell` for scripts and shell pipelines

**Common Mistake**

Using the `shell` module for every task unnecessarily increases security risks.

---

### Question 8

**Question**

What is the purpose of the `copy` and `template` modules?

**Answer**

The `copy` module copies files exactly as they are.

The `template` module copies Jinja2 template files after replacing variables.

**Explanation**

Use:

- `copy` for static files
- `template` for dynamic configuration files

**Used in Production**

Deploying configuration files that differ between Development, Testing, and Production environments.

---

### Question 9

**Question**

What is the purpose of the `service` module?

**Answer**

The `service` module manages Linux services.

Example:

```yaml
service:
  name: nginx
  state: started
```

**Explanation**

It can:

- Start
- Stop
- Restart
- Reload
- Enable
- Disable services

**Used in Production**

Managing application services after deployments.

---

### Question 10

**Question**

What is the purpose of the `package`, `apt`, and `yum` modules?

**Answer**

- `package` is a generic package management module.
- `apt` is used for Debian/Ubuntu.
- `yum` is used for RHEL/CentOS.

**Explanation**

The `package` module automatically uses the appropriate package manager based on the operating system.

**Used in Production**

Installing:

- Nginx
- Apache
- Docker
- Git
- Monitoring agents

**Common Mistake**

Using the `apt` module on RHEL systems or the `yum` module on Ubuntu systems.

---

### Question 11

**Question**

What are the purposes of the `user` and `git` modules?

**Answer**

The `user` module manages Linux user accounts.

Example:

```yaml
user:
  name: devops
  state: present
```

The `git` module clones or updates Git repositories.

Example:

```yaml
git:
  repo: https://github.com/example/app.git
  dest: /opt/app
```

**Explanation**

These modules simplify common administrative and deployment tasks.

**Used in Production**

- Creating service accounts
- Deploying application source code

---

### Question 12

**Question**

Why should you prefer Ansible modules over raw shell commands?

**Answer**

Modules are:

- Idempotent
- More secure
- Easier to read
- Cross-platform
- Better integrated with Ansible

**Explanation**

Modules understand the desired state and only make changes when necessary.

**Used in Production**

Professional Ansible playbooks primarily use modules instead of shell scripts.

**Common Mistake**

Many beginners rely heavily on the `shell` module instead of using dedicated Ansible modules.

---

# Scenario-Based Interview Questions

### Scenario 1

**Question**

Your playbook must install Apache on Ubuntu servers and HTTPD on RHEL servers. How would you avoid maintaining two separate playbooks?

**Answer**

Use Ansible Facts to detect the operating system and variables to define the appropriate package name.

**Explanation**

Facts enable OS-specific automation while maintaining a single reusable playbook.

---

### Scenario 2

**Question**

A task checks whether Docker is installed, and the next task should execute only if Docker is missing. How can you achieve this?

**Answer**

Store the output using a Registered Variable and use a conditional (`when`) in the following task.

**Explanation**

Registered variables allow decisions based on previous task results.

---

### Scenario 3

**Question**

Your application configuration file contains different database hostnames for Development and Production. Which module should you use?

**Answer**

Use the `template` module with variables.

**Explanation**

Templates generate dynamic configuration files for different environments.

---

### Scenario 4

**Question**

You need to copy the same SSL certificate to every server without modifying its contents. Which module would you use?

**Answer**

Use the `copy` module.

**Explanation**

The certificate is static, so no variable substitution is required.

---

### Scenario 5

**Question**

A developer uses the `shell` module for every task in a playbook. What recommendation would you make?

**Answer**

Use dedicated Ansible modules whenever possible and reserve the `shell` module only for commands requiring shell-specific features.

**Explanation**

Modules are safer, idempotent, and easier to maintain.

---

### Scenario 6

**Question**

Your playbook installs a package successfully but fails to start the service. Which module should be used for the second task?

**Answer**

Use the `service` module.

**Explanation**

Package installation and service management are separate tasks handled by different modules.

---

### Scenario 7

**Question**

A team manages both Ubuntu and CentOS servers. Which package module provides the best portability?

**Answer**

Use the generic `package` module.

**Explanation**

It automatically invokes the appropriate package manager based on the operating system.

---

### Scenario 8

**Question**

Your deployment pipeline must clone the latest application source code from GitHub before deployment. Which module should you use?

**Answer**

Use the `git` module.

**Explanation**

The `git` module efficiently clones or updates repositories without requiring shell commands.

---

### Scenario 9

**Question**

Your playbook creates an application user account before deploying software. Which module is appropriate?

**Answer**

Use the `user` module.

**Explanation**

The `user` module manages Linux user accounts in an idempotent manner.

---

### Scenario 10

**Question**

An inventory variable defines `package_name=nginx`, but the playbook receives `package_name=httpd` through `--extra-vars`. Which value will Ansible use?

**Answer**

Ansible uses the value passed through `--extra-vars` because it has higher variable precedence.

**Explanation**

Understanding variable precedence is essential for predicting playbook behavior and avoiding configuration conflicts.
