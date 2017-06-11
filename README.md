mvitale1989.docker-compose-target
=================================

Deploy a local docker-compose project to a remote host, without needing the
remote engine to listen on a TCP port.

Instead of contacting the remote engine by means of its TCP port, this role
copies over your docker-compose project directory and deploys it from the remote
machine itself. It is functionally equvalent to executing `docker-compose up` on
the remote host.


Requirements
------------

The docker engine must be installed on the remote host, and should be listening
on a unix-domain socket (default settings).


Role variables
--------------

- `project`: the path to your docker-compose project.
- `dct_recreate`: if some files of your docker-compose project change, they will
  be transferred to the remote host, but the container rebuild logic might not
  detect their change. To force a rebuild and redeploy of your projects, use
  `-e { dct_recreate: True }` while launching the `ansible-playbook` program.


Example Playbook
----------------

    - hosts: docker-server.example.com
      roles:
        - { role: mvitale1989.docker-compose-target, project: files/project1  }
        - role: mvitale1989.docker-compose-target
          project: ../../docker-compose-projects/project2


Dependencies
------------

- `docker_service` ansible module


License
-------

BSD


Author informations
-------------------

[https://github.com/mvitale1989][1]

[1]: https://github.com/mvitale1989
