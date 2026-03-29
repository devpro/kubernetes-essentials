# Security in Kubernetes

[kubernetes.io/docs/concepts/security](https://kubernetes.io/docs/concepts/security/)

## Authentication

Two types of accounts:

- Users through the kube-apiserver
  - Authentication mechanism
    - static password files: kube-apiserver `--basic-auth-file` start argument (csv file)
    - static token files: kube-apiserver `--token-auth-file` start argument (csv file)
    - certificates
    - identity services
- Service Accounts

See:

- [A Kubernetes engineer’s guide to mTLS by Buoyant](https://buoyant.io/mtls-guide/)

## Certificates

```bash
# view a certificate
openssl x509 -in <certificate path> -text

# for example to view the Common Name (CN) configured on the Kube API Server Certificate
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout
```

Certificates folders: /etc/kubernetes/pki (control plane), /var/lib/kubelet/pki (workder node)

## Roles

```bash
# check if a user can do actions
k get pods --as dev-user
```

## Operators

- [Kubernetes Security Profiles Operator](https://github.com/kubernetes-sigs/security-profiles-operator)

## Tools

- [Popeye](https://github.com/derailed/popeye)
- [kubeaudit](https://github.com/Shopify/kubeaudit)
- [kube-bench](https://github.com/aquasecurity/kube-bench)

## Concepts

### Terminology

Abbreviation | Meaning                                     | Links
-------------|---------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------
**CIS**      | Center for Internet Security                | [CIS Kubernetes Benchmarks](https://www.cisecurity.org/benchmark/kubernetes)
**CVE**      | Common Vulnerabilities and Exposures        | [cve.org](https://www.cve.org/)
**DLP**      | Data Loss Prevention                        | [What is DLP?](https://www.imperva.com/learn/data-security/data-loss-prevention-dlp/) (example: Social Security Number (SSN))
**DPI**      | Deep Packet Inspection                      | [What is DPI?](https://www.fortinet.com/resources/cyberglossary/dpi-deep-packet-inspection)
**eBPF**     |                                             | [ebpf.io](https://ebpf.io/), [eBPF: Put the Kubernetes Data Plane in the Kernel](https://thenewstack.io/ebpf-put-the-kubernetes-data-plane-in-the-kernel/)
**FIPS**     | Federal Information Process Standard        | -
**FISMA**    | Federal Information Security Management Act | -
**IAM**      | Idendity and Access Management              | -
**IDS**      | Intrusion Systems                           | -
**IPS**      | Intrusion Prevention Systems                | -
**OWASP**    | Open Web Application Security Project       | [owasp.org](https://owasp.org/)
**OSI**      | Open Systems Interconnection                | [OSI Model Explained](https://www.youtube.com/watch?v=LANW3m7UgWs&t=13s)
**SIEM**     | Security Information and Event Managers     | -
**WAF**      | Web Application Firewall                    | [What is a WAF?](https://www.cloudflare.com/learning/ddos/glossary/web-application-firewall-waf/)

### Securization logic

- Principles
  - Least privilege
  - Zero-Trust

- 3 steps of authentication security
  - Authentication
  - Authorization
  - Admission

- Network traffic
  - North-South
  - East-West

### Checklists

- [15 Point Kubernetes Security Checklist](https://containerjournal.com/editorial-calendar/rsa/15-point-kubernetes-security-checklist/) - May 5, 2021
