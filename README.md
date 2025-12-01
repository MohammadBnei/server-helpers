# Ansible Helpers for Pigsty Management

This repository contains Ansible playbooks to simplify common management tasks for a Pigsty PostgreSQL cluster, specifically creating users and databases by modifying the `pigsty.yml` configuration and triggering Pigsty's deployment.

## Prerequisites

* **Ansible:** Installed on your local machine.
* **SSH Access:** Configured for `dserver` from your local machine, without requiring a password (e.g., using SSH keys).
* **Pigsty Installation:** A running Pigsty installation on `dserver`, with the `pigsty.yml` file and `bin/` directory accessible at the paths specified in the playbooks.

## Configuration

* `ansible/inventory/hosts.ini`: Defines the target server (`dserver`).
* `ansible/ansible.cfg`: Basic Ansible configuration.
* `ansible/playbooks/`: Contains the playbooks for specific tasks.

**Important:** Before running any playbook, ensure the `pigsty_config_path` variable within each playbook (`create_pg_user.yml`, `create_pg_db.yml`) is correctly set to the base path of your Pigsty installation on `dserver`.

## Usage

Navigate to the root of this repository in your terminal.

### 1. Create a PostgreSQL User

This playbook will prompt you for user details, update the `pigsty.yml` on `dserver`, and optionally run the Pigsty command to create the user.

```console
ansible-playbook -i ansible/inventory/hosts.ini ansible/playbooks/create_pg_user.yml
```

### 2. Create a PostgreSQL Database

This playbook will prompt you for database details (name, owner, comment, extensions), update the `pigsty.yml` on `dserver`, and optionally run the Pigsty command to
create the database.

```console
ansible-playbook -i ansible/inventory/hosts.ini ansible/playbooks/create_pg_db.yml
```
