# cowpoke

> Experiments with Rancher in Vagrant

## Prerequisites

Versions tested:

* Vagrant 1.8.5
* VirtualBox 5.1.4

For virtualbox providers, make sure the `vagrant-vbguest` plugin is installed

    vagrant plugin install vagrant-vbguest

## Running

> Based on the [Rancher Quick Start Guide][RQSG]

[RQSG]: http://docs.rancher.com/rancher/latest/en/quick-start-guide/

Start up the machine with the following commands

    vagrant up --no-provision
    vagrant reload

It'll take a while to load up. If you want to check, run the following command:

    vagrant ssh --command 'docker logs -f rancher-server'

You're looking for a line saying `... Startup Succeeded, Listening on port ...`

You should now be able to follow the instructions below:

1. Browse to `http://localhost:8080`.
2. Navigate to __Infrastructure__ &xrarr; __Hosts__
3. Click __Add Host__
4. Set the host registration url server to the host machine's IP address.
   Make sure you add the scheme and port!
5. Select __Custom__
6. Paste the host IP address into the public IP box.
7. Copy the command that Rancher is presenting to you.
8. Connect to the vagrant box
        vagrant ssh
9. Run the command copied from Rancher. It will add a new docker container,
   first pulling the images then starting the agent and registering.
   It'll take a while.
