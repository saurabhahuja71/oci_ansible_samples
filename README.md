# Ansible OCI Tutorial: Oracle Cloud Automation Playbooks for Students

**Ansible for Oracle Cloud Infrastructure (OCI)** sample playbooks—list **Object Storage buckets**, query **compute shapes**, work with **namespaces**, install **httpd**, and explore **custom image** setup/teardown. Built for college DevOps and cloud automation labs.

> **Lab 2** in the [Terraform & IaC learning path](https://github.com/saurabhahuja71/learning-path#5-terraform--infrastructure-as-code) · Audience: intermediate beginners · Time: ~2–4 hours · Level: intermediate

## What is this repository?

A set of **Ansible YAML playbooks** using the `oracle.oci` collection patterns (`connection: local`, localhost control node) plus simple Linux config examples (`httpd`).

**SEO keywords:** *Ansible OCI tutorial*, *Oracle Cloud Ansible playbooks*, *oci_object_storage_bucket_facts*, *Ansible automation for beginners*, *DevOps college lab Ansible*.

## Playbooks / files (overview)

| File / folder | Purpose |
|---------------|---------|
| `getbuckets.yml` | List Object Storage buckets (namespace + facts) |
| `getns.yml` | Namespace helpers |
| `getADs.yml` | Availability domains |
| `getcomputeshapes.yml` | Compute shape facts |
| `bucketsloop.yml` | Loop patterns over buckets |
| `container.yaml` | Container-related sample |
| `httpd.yml` | Install/enable Apache httpd on a host |
| `install.yml` / `createfile.yml` / `remotehost.yaml` | General automation sketches |
| `demo.oci.yaml` | Demo entry |
| `oci_custom_image_sample/` | `setup.yaml` / `teardown.yaml` / `sample.yaml` |

## Prerequisites

- Python 3 + **Ansible** 2.12+  
- `ansible-galaxy collection install oracle.oci` (or equivalent OCI Ansible collection)  
- OCI credentials available to the collection (API key / config)  
- Optional: Linux target hosts for `httpd.yml`  

**Previous lab:** [oci_terraform_samples](https://github.com/saurabhahuja71/oci_terraform_samples)

## Quick start

```bash
git clone https://github.com/saurabhahuja71/oci_ansible_samples.git
cd oci_ansible_samples

# install collection (once)
ansible-galaxy collection install oracle.oci

# edit compartment_id / vars inside the playbook before running
ansible-playbook getbuckets.yml -v
```

Example idea from `getbuckets.yml`:

1. Get Object Storage **namespace** facts  
2. List **bucket** facts for a compartment  
3. `debug` the result  

For Linux package demos:

```bash
# only against hosts you own — update inventory first
ansible-playbook httpd.yml -i your_inventory.ini
```

## What you will learn

- Ansible playbook structure (`hosts`, `tasks`, `vars`)  
- OCI facts modules vs Terraform resources (query vs declare)  
- When to use Ansible (config/drift) vs Terraform (provision)  
- Idempotent service installs (`httpd` example)  

## Lab exercises

1. Fill in a real `compartment_id` and successfully list buckets.  
2. Add a task that creates a bucket only if missing (check collection docs).  
3. Convert `httpd.yml` to use handlers correctly end-to-end.  
4. Write a one-pager: *Terraform vs Ansible on OCI*.  
5. Next cloud VM lab: [terraform-azure-jenkins-sample](https://github.com/saurabhahuja71/terraform-azure-jenkins-sample).

## Learning path

| # | Lab | Focus |
|---|-----|--------|
| 1 | [oci_terraform_samples](https://github.com/saurabhahuja71/oci_terraform_samples) | Provision with Terraform |
| **2 (this)** | oci_ansible_samples | Automate / query with Ansible |
| 3 | [terraform-azure-jenkins-sample](https://github.com/saurabhahuja71/terraform-azure-jenkins-sample) | Azure Jenkins |
| 4 | [github-action-demo](https://github.com/saurabhahuja71/github-action-demo) | CI with Actions |

Hub: [learning-path](https://github.com/saurabhahuja71/learning-path)

## FAQ — Ansible + OCI

**Do I need a remote VM for every playbook?**  
No. Many OCI modules use `connection: local` and talk to the OCI API from your laptop.

**Collection name changed?**  
Oracle’s Ansible content evolves—check current docs if a module is renamed.

**Is this production automation?**  
Teaching samples—add linting, CI, secrets managers, and least privilege before prod.

## Topics / SEO tags

`ansible` `oci` `oracle-cloud` `automation` `devops` `playbooks` `tutorial` `infrastructure` `college` `education` `object-storage`

## Author

[Saurabh Ahuja](https://github.com/saurabhahuja71) · [learning-path](https://github.com/saurabhahuja71/learning-path)

## License

Educational sample.
