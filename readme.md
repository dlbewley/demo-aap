# How to install Ansible Automation Platform to OpenShift

## Install

*YMMV*

* [Install the operator](install/operator). This process relies heavily on the Red Hat [GitOps Catalog](https://github.com/redhat-cop/gitops-catalog/tree/main/ansible-automation-platform).

```bash
oc apply -k operator
```

* [Install an instance](install/instance) of the Controller and Hub (optional

```bash
oc apply -k instance
```

* Controller? Hub? Both? _Adam Pippert_
> "Hub acts as a content manager for Ansible.  It connects to container repos for execution environments, controls access to content, and allows you to pull certified and validated content from Red Hat.  Controller controls how individual playbooks are run against your execution environment and how they’re run."

### Caveats

* Namespace may be `aap` or it may be `ansible-automation-platform`
* If your default storageclass is ceph-rbd you will have a problem, this patch fixes it [install/instance/patch-automationcontroller.yaml](install/instance/patch-automationcontroller.yaml)
* You must update the URL in the console links. That is done here [install/instance/patch-consolelink.yaml](install/instance/patch-consolelink.yaml)

## Login and License

* Obtain the login password for the Controller interface

```bash
oc extract secret/controller-admin-password -n ansible-automation-platform --to=-
# password
EXAMPLE
```

* Go get a trial license <https://www.redhat.com/en/technologies/management/ansible/trial> 
* Once you have a sub visible in your [subscription manager](https://access.redhat.com/management/) put RH password into Controller interface and it will download it automatically

## Getting Started Using AAP

* TBD :)