# **Ansible-NodeMultiUserEnv**

Ansible-NodeMultiUserEnv is an Ansible role for installing and configuring a multi-user NodeJS environment as written in [this](https://www.nixknight.com/2018/03/multi-user-nodejs-environment/) blog post for Debian and Ubuntu systems.

## **Requirements**

At the moment this role doesn't depend on anything.

## **Role Variables**

There are 5 role variables:
```
NODE_VERSION
INSTALL_NODEJS
ENABLE_SRC_REPO
MODIFY_SYSTEM_SKEL
MODIFY_USER_ENV
```
* `NODE_VERSION` variable stores NodeJS repo version. By default its set to `node_8.x` as, at the time of this writing, its the LTS version. You may change this in conjunction with `INSTALL_NODEJS` variable if you want this role to install NodeJS.
* `INSTALL_NODEJS` variable contains a boolean value which helps the role decide wether or not to install NodeJS on the system. By default its set to `True`.
* `ENABLE_SRC_REPO` variable contains a boolean value which helps the role decide wether or not to enable NodeJS source repository. By default this variable is set to `False`.
* `MODIFY_SYSTEM_SKEL` variable contains a boolean value which helps the role decide wether or not to make adjustments to `/etc/skel` directory so that all future users can have their own NodeJS environment. By default this value is set to `True`. Note that the users will be using NodeJS version installed system-wide.
* `MODIFY_USER_ENV` variable contains a boolean value which helps the role decide wether to make adjustments to existing users of a system. This makes modifications in user environments similar to `MODIFY_SYSTEM_SKEL`. By default this variable is set to `False`. You need to define a list of users to make it work. Example is as follows:

## **Dependencies**

This role doesn't depends on any other role for execution.

## **Example Playbook**

An example of running the role is as follows:
```yml
    - hosts: servers
      gather_facts: True
      roles:
        - role: NodeMultiUserEnv
          MODIFY_SYSTEM_SKEL: False
          MODIFY_USER_ENV: True
          USERS:
            - test1
            - test2
            - test3
```

## **License**

This playbook is licensed under MIT License (See the LICENSE file).

## **Author**

[Saad Ali](https://github.com/nixknight)
