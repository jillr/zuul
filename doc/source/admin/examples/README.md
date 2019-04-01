# Zuul Example for Ansible POCs
Brings up a Zuul / Gerrit environment that can be used for Ansible using
the upstream Zuul [quick-start](https://zuul-ci.org/docs/zuul/admin/quick-start.html)
.
# Pre-requisites
A host / VM to be a static node for Zuul to run tests on (the static node
Docker image the quick-start comes with is missing things that VMWare needs).
Add that host IP and host-key to 
`doc/source/admin/examples\etc_nodepool/nodepool.yaml`.

`apt install git-review`

# Usage 
`cd zuul/doc/source/admin/examples ; sudo -E docker-compose up`

Follow the instructions at the Zuul [quick-start guide](https://zuul-ci.org/docs/zuul/admin/quick-start.html)
to get users and keys set up.

Clone the Ansible project from Gerrit (this ensures your .gitreview and
remotes are setup correctly for Gerrit.)

`git clone http://localhost:8080/ansible`

Pull upstream into the new repo.

`git remote add upstream  https://github.com/ansible/ansible`
`git pull upstream devel`

Commit into Gerrit.

`git review`

You are now able to add tests, and zuul will run them.
