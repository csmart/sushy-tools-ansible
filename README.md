<!-- vim-markdown-toc GFM -->

* [Install and start Sushy Tools](#install-and-start-sushy-tools)
	* [Get the code](#get-the-code)
		* [Run the code](#run-the-code)

<!-- vim-markdown-toc -->

# Install and start Sushy Tools

This is an example Ansible playbook for my simple [Sushy Tools Ansible
role](https://github.com/csmart/ansible-role-sushy-tools) (and only tested on
Fedora, sorry).

It will use `pip` to install Sushy Tools as root and configure it to talk to
`libvirtd`.

You can set a few variables:

 - `sushy_user` - the user to run as, defaults to `root` (note that a non-root user will need to be able to talk to `libvirtd` unauthenticated)
 - `sushy_ip` - the IP address to bind to, defaults to `0.0.0.0`
 - `sushy_port` - the port to listen on, defaults to `8080`

It will also open the port in `firewalld`, if it is running.

## Get the code

Get the code, which will pull in the role automatically.

```bash
git clone --recursive https://github.com/csmart/sushy-tools-ansible.git
cd sushy-tools-ansible
```

If you already have the code, then pull in the latest code and update the submodule.

```bash
git pull
git submodule update
```

### Run the code

Run against localhost, with no extra args:

```bash
./run.sh -i localhost, -c local
```

Run against remote host (e.g. `kvmhost`), setting some extra args:

```bash
./run.sh -i kvmhost, -e "sushy_port=8888 sushy_user=${USER}"
```
