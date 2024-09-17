# Galaxy SlurmScale

TODO: docs

For now, the magic:

Populate a file in `group_vars/all/` that sets:

```yaml
---

slurm_scale_tailscale_authkey: tskey-auth-...
ceph_galaxy_scratch_key: AQ...

ceph_mounts: ...

jetstream_local_controller_address: ...
jetstream_local_cvmfs_stratum1_address: ...
jetstream_local_cvmfs_proxy_address: ...
```

And place the munge key in `files/slurm/munge.key`.

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
