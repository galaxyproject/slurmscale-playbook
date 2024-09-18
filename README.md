# Galaxy SlurmScale

TODO: docs

For now, the magic:

Populate a file in `group_vars/all/` that sets:

```yaml
---

slurm_scale_tailscale_authkey: tskey-auth-...
ceph_mounts: ...
galaxy_cvmfs_server_urls: ...
cvmfs_http_proxies: ...
```

And place the munge key in `files/slurm/munge.key`.

For usegalaxy.org this is deployed with the [slurmscale role in infrastructure-playbook](https://github.com/galaxyproject/infrastructure-playbook/tree/main/roles/slurmscale).

## How to use:

Build image(s):


```console
ansible-playbook -i inventory/image-builders.yaml playbook-image.yaml [--limit=usegalaxy-node]
```

Resume:

```console
ansible-playbook -i js2-tiny0, -l js2-tiny0 playbook-resume.yaml
```

Suspend:

```
ansible-playbook -i inventory/openstack.yaml -l js2-tiny0 playbook-suspend.yaml
```
