# Ansible for Shadowsocks w/ v2ray

## Usage

0. Install Ansible.

1. Configure your `hosts` file. Things for you to change are:

``` yaml
# See hosts.example.yml
ansible_ssh_host: "examp.le"  # Server address (must be a domain)
ansible_ssh_private_key_file: # SSH key file of server (optional)
ansible_user: ubuntu          # User to login
ss_password: "youbet"         # shadowsocks: password
ss_server_port: 8883          # shadowsocks: port
ss_method: "chacha20-ietf-poly1305" # shadowsocks: encryption method
v2_ws_path: "wtfismyip"       # v2ray: Websocket path
v2_id: "deadbeef-dead-beef-deba-deadbeefbeef" # v2ray: user id (UUID)
v2_local_port: 9999           # v2ray: Local listen port on the server
v2_alterid: 64                # v2ray: alterid
acme_sh_account_email: ""     # ACME account email (optional)
```

And save it to `hosts.yml`.

2. Run:

```
ansible-playbook -i hosts.yml deploy_all.yml all
```

## Notice

It is designed to run on Ubuntu (for example, ami-0302a0802f3af99c3 on AWS) currently.