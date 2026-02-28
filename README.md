# [Ansible role jitsi](#ansible-role-jitsi)

Install and configure jitsi on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-jitsi/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-jitsi/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-jitsi/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-jitsi)|[![downloads](https://img.shields.io/ansible/role/d/buluma/jitsi)](https://galaxy.ansible.com/buluma/jitsi)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-jitsi.svg)](https://github.com/buluma/ansible-role-jitsi/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-jitsi/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
  - role: buluma.jitsi
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-jitsi/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: false

  roles:
  - role: buluma.bootstrap
  - role: buluma.ca_certificates
  - role: buluma.java
  - role: buluma.hostname
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-jitsi/blob/master/defaults/main.yml):

```yaml
---
# defaults file for jitsi

# You can choose to install different release: `stable`, `testing` or `nightly`.
jitsi_release: stable

# Settings used for the installation of jitsi-meet
jitsi_settings:
  - name: jitsi-meet
    question: jitsi-meet/cert-choice
    value: "Generate a new self-signed certificate (You will later get a chance to obtain a Let's encrypt certificate)"
    type: string
  - name: jitsi-meet
    question: jitsi-meet/jvb-serve
    value: true|bool
    type: boolean
  - name: jitsi-meet-prosody
    question: jitsi-meet-prosody/jvb-hostname
    value: "{{ ansible_fqdn }}"
    type: string
  - name: jitsi-videobridge
    question: jitsi-videobridge/jvb-hostname
    value: "{{ ansible_fqdn }}"
    type: string
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-jitsi/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.ca_certificates](https://galaxy.ansible.com/buluma/ca_certificates)|[![Build Status GitHub](https://github.com/buluma/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-ca_certificates/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-ca_certificates/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-ca_certificates)|
|[buluma.java](https://galaxy.ansible.com/buluma/java)|[![Build Status GitHub](https://github.com/buluma/ansible-role-java/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-java/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-java/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-java)|
|[buluma.hostname](https://galaxy.ansible.com/buluma/hostname)|[![Build Status GitHub](https://github.com/buluma/ansible-role-hostname/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-hostname/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-hostname/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-hostname)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-jitsi/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-jitsi/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-jitsi/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)
