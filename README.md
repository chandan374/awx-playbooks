# awx-playbooks

32504
kubectl get svc -l "app.kubernetes.io/managed-by=awx-operator"
kubectl get secret awx-demo-admin-password -o jsonpath="{.data.password}" -n awx | base64 --decode ; echo





http://localhost:32504/

aUg51Ke9H4Du7UBVdUo9dAH0vRv1iIRk


# - name: Debug: show list of private hosts
#   ansible.builtin.debug:
#     var: groups['private_hosts']

# - name: Fail if no private hosts found
#   ansible.builtin.fail:
#     msg: "No private hosts found in 'private_hosts' group!"
#   when: groups['private_hosts'] | length == 0

# - name: Loop through private hosts and install nginx via SSH
#   vars:
#     private_hosts: "{{ groups['private_hosts'] }}"
#   block:
#     - name: Create temp dir on jump host
#       ansible.builtin.shell: mktemp -d /tmp/nginx-setup-XXXXXX
#       register: tmp_dir
#       changed_when: true

#     - name: Set script path
#       set_fact:
#         remote_script_path: "{{ tmp_dir.stdout }}/install_nginx.sh"

#     - name: Copy nginx install script to jump host
#       ansible.builtin.template:
#         src: install_nginx.sh.j2
#         dest: "{{ remote_script_path }}"
#         mode: '0755'
#       vars:
#         remote_host: "{{ item }}"

#     - name: Run install script on private host {{ item }}
#       ansible.builtin.shell: |
#         ssh -o StrictHostKeyChecking=no ec2-user@{{ item }} {{ remote_script_path }}
#       register: install_result
#       vars:
#         remote_host: "{{ item }}"

#     - name: Show install result from {{ item }}
#       ansible.builtin.debug:
#         var: install_result.stdout_lines

#     # - name: Clean up script after execution
#     #   ansible.builtin.file:
#     #     path: "{{ tmp_dir.stdout }}"
#     #     state: absent
#   loop: "{{ private_hosts }}"
#   loop_control:
#     label: "{{ item }}"
