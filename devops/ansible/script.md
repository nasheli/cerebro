http://docs.ansible.com/script_module.html

# Example from Ansible Playbooks
- script: /some/local/script.sh --some-arguments 1234

# Run a script that creates a file, but only if the file is not yet created
- script: /some/local/create_file.sh --some-arguments 1234 creates=/the/created/file.txt

# Run a script that removes a file, but only if the file is not yet removed
- script: /some/local/remove_file.sh --some-arguments 1234 removes=/the/removed/file.txt
