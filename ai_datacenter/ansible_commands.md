## Ad-hoc commands
Ad-hoc commands are quick, single-line commands used to perform tasks on managed nodes without a playbook.

### Command	Description

ansible all -m ping	Tests connectivity to all hosts in the inventory.

ansible webservers -m shell -a "uptime"	Runs the uptime command on hosts in the webservers group.

ansible all -m setup	Gathers system facts (information) from all managed nodes.

ansible webservers -m file -a "path=/tmp/test.txt state=touch"	Creates an empty file named test.txt in /tmp on webservers.

ansible dbservers -m apt -a "name=postgresql state=present"	Installs the postgresql package on hosts in the dbservers group (for Debian/Ubuntu).

ansible dbservers -m service -a "name=postgresql state=restarted"	Restarts the postgresql service on the database servers.

ansible all -m copy -a "src=/tmp/foo dest=/tmp/bar"	Copies a file from the control node to all managed nodes.

## Playbook commands
Playbooks are the core of Ansible automation, enabling complex, repeatable tasks.

### Command	Description

ansible-playbook playbook.yml	Runs a specified playbook.

ansible-playbook playbook.yml --check	Performs a "dry run" to show what changes would be made without executing them.

ansible-playbook playbook.yml --syntax-check	Checks the playbook for syntax errors.

ansible-playbook playbook.yml --limit webservers	Runs the playbook only on hosts in the webservers group.

ansible-playbook playbook.yml --start-at-task "Install packages"	Starts execution at a specific task named "Install packages".

ansible-playbook playbook.yml --extra-vars "version=1.2.3"	Passes additional variables to the playbook at runtime.

ansible-playbook playbook.yml --tags "nginx, database"	Runs only the tasks marked with the nginx and database tags.

## Inventory management

Manage and view your hosts and groups with these commands.

### Command	Description

ansible-inventory --list	Shows a full JSON representation of your inventory.

ansible-inventory --graph	Displays the inventory as a graphical tree.

ansible-inventory --host webserver1	Shows detailed variables and groups for a single host.

## Ansible Vault

Ansible Vault is used to encrypt and protect sensitive data like passwords and API keys.

### Command	Description

ansible-vault create secure.yml	Creates a new encrypted file.

ansible-vault edit secure.yml	Edits an existing encrypted file.

ansible-vault encrypt my_file.yml	Encrypts an existing plain text file.

ansible-vault decrypt secure.yml	Decrypts an encrypted file.

ansible-vault view secure.yml	Views the unencrypted contents of a vault file.

ansible-vault rekey secure.yml	Changes the password for an encrypted file.

ansible-vault encrypt_string 'MySecretString'	Encrypts a single string for use in a playbook or variable file.

## Configuration and debugging

These commands help you manage Ansible's configuration and troubleshoot issues.

### Command	Description

ansible --version	Displays the current Ansible version and configuration details, including the ansible.cfg path.

ansible-config list	Lists all available configuration settings and their default values.

ansible-config dump	Shows all current settings, including those overridden by ansible.cfg or environment variables.

ansible-playbook playbook.yml -v	Increases the verbosity of the output. Use -vvv or higher for more detailed debugging.

## Role management with Ansible Galaxy

Ansible Galaxy is the hub for discovering and sharing community-contributed roles.

### Command	Description

ansible-galaxy install geerlingguy.nginx	Installs a role from the Ansible Galaxy website.

ansible-galaxy list	Lists all installed roles.

ansible-galaxy init my_new_role	Creates the basic directory structure for a new role.

## Module documentation

Find documentation for any installed module.

### Command	Description

ansible-doc -l	Lists all available modules.

ansible-doc copy	Shows documentation for a specific module, like copy.

ansible-doc -s apt	Shows a usage snippet for the apt module.
