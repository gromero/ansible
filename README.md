### What does it provide?

When correctly executed this script will create a complete environment to build
TVM and microTVM from source. So once it's done one just needs to jump to
`~/git/tvm/build` and build TVM:

```sh
cd ~/git/tvm/build
cmake ..
make -j $(nproc)
```

### How should I execute it?

- Install Ansible in your local machine:

```sh
sudo apt-get install ansible
```

- Make sure you have ssh access (via ssh-key) and sudo in remote machine when
logging from the local machine, where you've just installed Ansible and from
where you're going to execute the script.

- Add the remote machine name (the same use to login via ssh) to Ansible's list
of hosts, i.e. `/etc/ansible/hosts`. For instance, if your remote machine is
called `dev0` your `/etc/ansible/hosts` file has to contain a section
`[tvm-dev]` listing `dev0`:

> [tvm-dev]
> dev0

- Clone this repo and run the `tvm.yml` playbook:

```sh
git clone https://github.com/gromero/ansible.git
cd ansible
ansible-playbook ./tvm.yml --ask-become-pass -vv
```

- Enter your sudo pass password when asked by Ansible

Once the playbook finishes OK, just jump to the machine and build TVM exactly
as instructed in "What does it provide?" section.
