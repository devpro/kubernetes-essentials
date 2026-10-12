# AppArmor

> AppArmor is a Linux kernel security module that supplements the standard Linux user and group based permissions to confine programs to a limited set of resources.
> AppArmor can be configured for any application to reduce its potential attack surface and provide greater in-depth defense.
> It is configured through profiles tuned to allow the access needed by a specific program or container, such as Linux capabilities, network access, file permissions, etc.
> Each profile can be run in either _enforcing_ mode, which blocks access to disallowed resources, or _complain_ mode, which only reports violations.
>
> &mdash; _[kubernetes.io/docs/tutorials/security/apparmor](https://kubernetes.io/docs/tutorials/security/apparmor/)_

✨ [AppArmor documentation](https://gitlab.com/apparmor/apparmor/-/wikis/Documentation)

🌐 [apparmor.net](https://www.apparmor.net/)

## Commands

```bash
# gives a high level status of AppArmor and applications it has profiles for
sudo aa-status

# discovers network servers that may or may not be confined
sudo aa-unconfined

# parses a file
sudo apparmor_parser /path/to/file

# gives a status
sudo apparmor_status
```

## Directories

Path               | Content
-------------------|--------
`/etc/apparmor/`   | Global and system settings
`/etc/apparmor.d/` | All the profiles, as well as profile 'chunks' that are commonly shared between profiles, that AppArmor will load on next boot
