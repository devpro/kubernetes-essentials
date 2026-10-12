# Falco

> **Falco** is a cloud native runtime security tool for Linux operating systems. It is designed to detect and alert on abnormal behavior and potential security threats in real-time.
>
> At its core, **Falco** is a kernel monitoring and detection agent that observes events, such as syscalls, based on custom rules. **Falco** can enhance these events by integrating metadata from the container runtime and Kubernetes. The collected events can be analyzed off-host in SIEM or data lake systems.
>
> &mdash; _[falco.org](https://falco.org/docs/)_

✨ [docs](https://falco.org/docs/)

![falco architecture v2](https://falco.org/docs/getting-started/images/falco-architecture-v2.png)

Read more: [IT Guide](https://github.com/devpro/information-technology-guide/blob/main/docs/foundations/cncf/falco.md)

## Configuration

✨ [Default and Local Rules Files](https://falco.org/docs/rules/default-custom/), [Default Rules](https://falco.org/docs/reference/rules/default-rules/)

`/etc/falco/falco.yaml` is the default configuration file.

It makes Falco load rules from the `/etc/falco/falco_rules.yaml` file, followed by any custom rules located in the `/etc/falco/rules.d` directory. This configuration is governed by the `rules_file` key:

```yaml
rules_file:
  - /etc/falco/falco_rules.yaml
  - /etc/falco/falco_rules.local.yaml
  - /etc/falco/rules.d
```
