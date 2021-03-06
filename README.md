modcloth.meetme_newrelic_plugin_agent
=========

This role installs and configures the MeetMe New Relic plugin agent
[https://github.com/MeetMe/newrelic-plugin-agent](https://github.com/MeetMe/newrelic-plugin-agent)

Requirements
------------

Any backend dependencies documented on
[https://github.com/MeetMe/newrelic-plugin-agent](https://github.com/MeetMe/newrelic-plugin-agent)
if you are collecting using those agents.

Role Variables
--------------
```yml
# non-standard plugin python packages required (see above)
meetme_newrelic_plugin_agent_backends:

# where to write the config file generated by the template
# also where the written upstart template will expect to find it
meetme_newrelic_plugin_agent_conf_path:

# the template to use (will not write a template if not set)
# because there are so many options available via the newrelic-plugin-agent conf
# this role is "bring your own template"
meetme_newrelic_plugin_agent_template:
```

Dependencies
------------

None.

Example Playbook
----------------

```yml
---
- hosts: all
  pre_tasks:
  - name: 'install monitor dependencies'
    apt: name="{{item}}" update_cache=yes
    with_items:
    - libpq-dev
    - python-dev

  roles:
  - role: modcloth.meetme-newrelic-plugin-agent
    meetme_newrelic_plugin_agent_backends:
    - postgresql
```

License
-------

MIT

Author Information
------------------

ModCloth, Inc.
