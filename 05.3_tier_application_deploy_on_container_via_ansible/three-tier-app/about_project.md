# Three-tier application using Ansible to deploy containers on a Docker server.

#### Step 1: Set Up Project Structure

```css
three-tier-app/
├── ansible.cfg
├── inventory
├── playbook.yml
├── roles/
│   ├── frontend/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   ├── files/
│   │   ├── templates/
│   │   └── vars/
│   │       └── main.yml
│   ├── backend/
│   │   ├── tasks/
│   │   │   └── main.yml
│   │   ├── files/
│   │   ├── templates/
│   │   └── vars/
│   │       └── main.yml
│   └── database/
│       ├── tasks/
│       │   └── main.yml
│       ├── files/
│       ├── templates/
│       └── vars/
│           └── main.yml
└── group_vars/
    └── all.yml
```

#### Command to create project structure

```css
mkdir -p three-tier-app/{roles/{frontend/{tasks,files,templates,vars},backend/{tasks,files,templates,vars},database/{tasks,files,templates,vars}},group_vars}
touch three-tier-app/{ansible.cfg,inventory,playbook.yml,group_vars/all.yml}
```

#### Step 2: Ansible Configuration File (ansible.cfg)
#### Step 3: Inventory File (inventory)
#### Step 4: Inventory File (inventory)

##### Explanation of Steps

```ini
01. Project Structure: This organizes the Ansible playbook, roles, and variables systematically.

02. Ansible Configuration: Specifies basic Ansible settings.

03. Inventory File: Lists the Docker server where the containers will be deployed.

04. Group Variables: Sets common variables used across all roles.

05. Playbook: Defines the main orchestration of roles (frontend, backend, database).

06. Role Definitions: Each role is responsible for deploying a specific tier of the application. The frontend uses Nginx, the backend uses a Python Flask app, and the database uses MySQL.

07. Application Files: These are the actual files needed for the backend application.

08. Running the Playbook: Executes the Ansible playbook to deploy the application on the Docker server.
```
This setup will deploy a simple three-tier application using Ansible to manage Docker containers.

