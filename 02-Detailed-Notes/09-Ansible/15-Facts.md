# Facts

## Overview

Ansible Facts are automatically collected pieces of information about managed hosts before Playbook execution. They describe the system's hardware, operating system, network configuration, memory, CPU, disks, and many other attributes.

Facts allow Playbooks to make intelligent decisions based on the current state of the target system.

For example, a Playbook can:

- Install different packages on Ubuntu and CentOS
- Configure network settings based on available interfaces
- Execute tasks only if enough memory is available

> **Interview Tip**
>
> Facts are one of the most frequently asked Ansible interview topics. They are automatically collected using the **setup module** unless fact gathering is disabled.

---

## Why It Is Used

Facts help to:

- Detect operating systems
- Identify hardware information
- Configure applications dynamically
- Support conditional execution
- Eliminate hardcoded values
- Enable environment-aware automation

---

## Architecture / Working

```mermaid
flowchart LR
    Playbook --> GatherFacts
    GatherFacts --> ansible_facts
    ansible_facts --> Tasks
    Tasks --> ManagedNodes
```

---

## Key Components

| Component | Purpose |
|-----------|---------|
| Facts | System information |
| ansible_facts | Dictionary storing collected facts |
| setup Module | Collects facts |
| gather_facts | Enables or disables fact collection |

---

## Types (if applicable)

Common Categories of Facts

- Operating System
- CPU
- Memory
- Disk
- Network
- Hostname
- Architecture
- Kernel
- Python Version

---

## Lifecycle / Workflow

```mermaid
flowchart LR
    StartPlaybook --> GatherFacts
    GatherFacts --> StoreFacts
    StoreFacts --> ExecuteTasks
```

---

## Configuration / Syntax (if applicable)

Default Behavior

```yaml
- hosts: web

  tasks:

    - debug:
        var: ansible_hostname
```

Disable Fact Gathering

```yaml
- hosts: web

  gather_facts: false
```

Use a Fact

```yaml
- debug:
    msg: "{{ ansible_distribution }}"
```

---

## Important Commands (if applicable)

Gather Facts

```bash
ansible all -m setup
```

View All Facts

```bash
ansible localhost -m setup
```

Filter Facts

```bash
ansible all -m setup -a "filter=ansible_hostname"
```

---

## Important Files (if applicable)

| File | Purpose |
|------|---------|
| Playbook | Uses collected facts |
| Inventory | Target hosts |

---

## Real-World Use Cases

- Install OS-specific packages
- Configure network interfaces
- Configure storage
- Generate configuration files
- Deploy environment-specific applications
- Hardware inventory reporting

---

## Advantages

- Dynamic automation
- Eliminates hardcoded values
- Supports multiple operating systems
- Improves Playbook flexibility
- Automatically collected

---

## Limitations

- Fact gathering slightly increases Playbook execution time
- Unnecessary facts consume memory
- Facts may become outdated during long-running Playbooks

---

## Common Interview Questions (Concept Only)

- What are Ansible Facts?
- When are Facts collected?
- Which module gathers Facts?
- Can Fact gathering be disabled?
- Why are Facts useful?

---

## Common Mistakes

- Assuming Facts are always available when `gather_facts` is disabled
- Using incorrect Fact names
- Collecting Facts when they are not required
- Hardcoding values instead of using Facts

---

## Troubleshooting

| Problem | Cause | Solution |
|----------|--------|----------|
| Undefined fact | Fact gathering disabled | Enable `gather_facts` |
| Incorrect value | Wrong Fact name | Verify using the `setup` module |
| Slow execution | Large Fact collection | Disable Facts if not needed |

Useful Commands

```bash
ansible all -m setup

ansible all -m setup -a "filter=*hostname*"
```

---

## Summary

Facts provide dynamic information about managed hosts and enable Playbooks to make intelligent, environment-aware decisions. They are automatically collected using the `setup` module unless disabled.

---

# Gather Facts

## Overview

Fact gathering is the process of automatically collecting system information before Playbook execution.

By default, Ansible performs this step at the beginning of every Play.

The collected information becomes available as Ansible Facts.

---

## Why It Is Used

Fact gathering allows Playbooks to:

- Detect operating systems
- Configure services dynamically
- Use hardware information
- Execute conditional tasks
- Support heterogeneous environments

---

## Architecture / Working

```mermaid
flowchart LR
    StartPlaybook --> GatherFacts
    GatherFacts --> SaveFacts
    SaveFacts --> ExecuteTasks
```

---

## Key Components

| Component | Purpose |
|-----------|---------|
| gather_facts | Controls fact collection |
| setup Module | Collects Facts |
| ansible_facts | Stores collected information |

---

## Types (if applicable)

Fact Gathering Options

- Enabled
- Disabled
- Manual gathering

---

## Lifecycle / Workflow

```mermaid
flowchart LR
    Start --> GatherFacts --> Tasks
```

---

## Configuration / Syntax (if applicable)

Enable Fact Gathering

```yaml
- hosts: web

  gather_facts: true
```

Disable Fact Gathering

```yaml
- hosts: web

  gather_facts: false
```

Manually Gather Facts

```yaml
- name: Gather Facts
  setup:
```

---

## Important Commands (if applicable)

Collect Facts

```bash
ansible all -m setup
```

---

## Important Files (if applicable)

Playbook

---

## Real-World Use Cases

- Multi-OS deployments
- Cloud provisioning
- Server auditing
- Dynamic configuration

---

## Advantages

- Automatic
- Dynamic
- Reliable
- Platform-aware

---

## Limitations

- Slightly slower Playbook startup
- Unnecessary in simple automation

---

## Common Interview Questions (Concept Only)

- What is `gather_facts`?
- Can Fact gathering be disabled?
- When are Facts collected?

---

## Common Mistakes

- Forgetting to enable Fact gathering after disabling it
- Using Facts before they are collected

---

## Troubleshooting

```bash
ansible all -m setup
```

---

## Summary

Fact gathering automatically collects host information before task execution and makes it available for use throughout the Playbook.

---

# ansible_facts

## Overview

`ansible_facts` is a dictionary that stores all information collected by the `setup` module.

Each system attribute becomes a key inside this dictionary.

Tasks access these values using Jinja2 expressions.

> **Interview Tip**
>
> Modern versions of Ansible expose Facts inside the `ansible_facts` dictionary, although many common Facts are also available as top-level variables for backward compatibility.

---

## Why It Is Used

The `ansible_facts` dictionary helps to:

- Access host information
- Configure systems dynamically
- Create conditional automation
- Generate templates

---

## Architecture / Working

```mermaid
flowchart LR
    SetupModule --> ansible_facts
    ansible_facts --> Playbook
```

---

## Key Components

| Component | Purpose |
|-----------|---------|
| ansible_facts | Stores collected Facts |
| Dictionary Keys | Individual system values |

---

## Types (if applicable)

Common Facts

- Hostname
- Distribution
- IP Address
- Memory
- CPU
- Kernel
- Architecture

---

## Lifecycle / Workflow

```mermaid
flowchart LR
    GatherFacts --> StoreInDictionary --> ReadFacts
```

---

## Configuration / Syntax (if applicable)

Display All Facts

```yaml
- debug:
    var: ansible_facts
```

Display Hostname

```yaml
- debug:
    msg: "{{ ansible_facts.hostname }}"
```

Display Operating System

```yaml
- debug:
    msg: "{{ ansible_facts.distribution }}"
```

---

## Important Commands (if applicable)

```bash
ansible all -m setup
```

---

## Important Files (if applicable)

Playbook

---

## Real-World Use Cases

- Conditional package installation
- Template generation
- Inventory reporting
- Dynamic service configuration

---

## Advantages

- Centralized system information
- Easy access
- Dynamic automation

---

## Limitations

- Large dictionary
- Some keys differ across operating systems

---

## Common Interview Questions (Concept Only)

- What is `ansible_facts`?
- How do you display all collected Facts?
- What type of data structure is `ansible_facts`?

---

## Common Mistakes

- Incorrect Fact names
- Case-sensitive key errors
- Using unavailable Facts

---

## Troubleshooting

```bash
ansible all -m setup
```

---

## Summary

`ansible_facts` is the dictionary that stores all system information collected by Ansible, enabling dynamic and intelligent automation.

---

# setup Module

## Overview

The `setup` module is the Ansible module responsible for collecting Facts from managed hosts.

It executes automatically before most Playbooks unless fact gathering is disabled.

The module can also be executed manually to inspect system information.

---

## Why It Is Used

The `setup` module helps to:

- Collect host information
- Verify connectivity
- Inspect system configuration
- Debug Playbooks
- Filter specific Facts

---

## Architecture / Working

```mermaid
flowchart LR
    setupModule --> CollectFacts
    CollectFacts --> ansible_facts
    ansible_facts --> Playbook
```

---

## Key Components

| Component | Purpose |
|-----------|---------|
| setup | Collects Facts |
| filter | Returns selected Facts |
| ansible_facts | Stores collected information |

---

## Types (if applicable)

Setup Operations

- Collect all Facts
- Collect filtered Facts

---

## Lifecycle / Workflow

```mermaid
flowchart LR
    ExecuteSetup --> CollectFacts --> ReturnFacts
```

---

## Configuration / Syntax (if applicable)

Run Setup Module

```bash
ansible all -m setup
```

Filter Hostname

```bash
ansible all -m setup -a "filter=ansible_hostname"
```

Filter Network Facts

```bash
ansible all -m setup -a "filter=ansible_default_ipv4"
```

Use in a Playbook

```yaml
- name: Collect Facts
  setup:
```

---

## Important Commands (if applicable)

Gather Facts

```bash
ansible all -m setup
```

Filter Facts

```bash
ansible all -m setup -a "filter=*memory*"
```

Display Hostname

```bash
ansible all -m setup -a "filter=ansible_hostname"
```

---

## Important Files (if applicable)

None

---

## Real-World Use Cases

- Server inventory
- Hardware auditing
- Operating system detection
- Troubleshooting
- Dynamic Playbook execution
- Configuration management

---

## Advantages

- Built into Ansible
- Automatic
- Comprehensive system information
- Supports filtering
- Easy troubleshooting

---

## Limitations

- Collecting all Facts may take additional time
- Large output can be difficult to navigate

---

## Common Interview Questions (Concept Only)

- What is the purpose of the `setup` module?
- Which module collects Facts?
- How do you filter specific Facts?
- Does the `setup` module run automatically?

---

## Common Mistakes

- Running the `setup` module unnecessarily in every task
- Forgetting to use filters for targeted output
- Assuming all Facts exist on every operating system

---

## Troubleshooting

| Problem | Cause | Solution |
|----------|--------|----------|
| No Facts returned | SSH or connection issue | Verify connectivity |
| Undefined Facts | Fact gathering disabled | Enable `gather_facts` or run `setup` manually |
| Large output | No filter applied | Use the `filter` parameter |

Useful Commands

```bash
ansible all -m setup

ansible all -m setup -a "filter=ansible_hostname"

ansible all -m setup -a "filter=*network*"
```

---

## Summary

The `setup` module is responsible for collecting system Facts from managed hosts. It powers dynamic automation by gathering detailed information that Playbooks can use for configuration, conditional execution, and environment-aware deployments.
