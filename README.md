# PiHole DNS Over HTTPS

This repository contains a simple Ansible Playbook to setup DNS over HTTPS for your Pi.Hole on your
ARM Raspberry Pi.

This is based on the instructions posted [here](https://docs.pi-hole.net/guides/dns-over-https/).

You can find the list of available DNS over HTTPS servers
[here](https://github.com/curl/curl/wiki/DNS-over-HTTPS).

## Usage

1. Install
    [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
    for your controlling machine.
1. Execute the playbook. The example below should be sufficient for most needs. If you want to
    override any variables, see the
    [CLI Documentation](https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html).

    - The `-i` flag specifies the server address of your Raspberry Pi. You can replace the
        `pi.hole` with your Pi's address. Remember to add a trailing `,` at the end to indicate
        that this is not a path to a file. See the user guide to
        [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html) for
        more information.
    - Change the `--user` flag for the user to SSH with in case you have a different username.
    - Add the `--ask-become-pass` flag if you have set a `sudo` password.

    ```bash
    ansible-playbook -i "pi.hole," \
        --user pi \
        site.yml
    ```
1. Configure Pi.hole to use the local `127.0.0.1#5533` DNS server.

    ![](https://docs.pi-hole.net/images/DoHConfig.png)
