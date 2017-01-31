Role Name
=========
[![Build Status](https://travis-ci.org/matic-insurance/ansible-deploy-notifications.svg?branch=master)](https://travis-ci.org/matic-insurance/ansible-deploy-notifications)

Ansible role to send notifications to the slack channel about deploy status. 
Role detects current user on host system to explain who triggered deploy

Requirements
------------

1. Get webhook url from slack and extract token part: 
  - URL: `https://hooks.slack.com/services/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`
  - Token is `T02FC8HRT/B3QTFE7E0/QA0mMNQv5kVJoAvEEE9Y2qSs`
  
2. Specify token as `notifications_slack_token` variable

Role Variables
--------------

Here is the list of default variables with default values:
```
notification_app_name: Unknown App
notification_environment_type: Unknown Instance
notification_deploy_info: deploying
notification_color: normal
```

Final slack message with these variables will look like: `Unknown App (Unknown Environment) deploying` 

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
- hosts: all
  gather_facts: false
  
  roles:
    - role: matic-insurance.deploy-notification
      notification_deploy_info: 'deploy started'
      notification_color: 'warning'
      notifications_slack_token: '{{ slack_token }}'
```

Actual task notification is executed only once on local host.
 
In our projects we have notification about start and end of deploy to see when deploy is finished

License
-------

MIT

Author Information
------------------

Matic is a communication platform that connects lenders and borrowers originating a new home loan. A borrower now knows where they are in the loan process and what they need to do to complete the loan.
