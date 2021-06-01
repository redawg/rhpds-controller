# rhpds-controller
This is a small repo for controlling/deploying RHPDS from Ansible controller

You will need the following created:

<B>Create Custom Creds - RHPDS  </B>

INPUT CONFIGURATION:
<pre class="line-number language-yaml"><code>fields:
  - id: username
    type: string
    label: Username
  - id: password
    type: string
    label: Password
    secret: true
   - id: url
    type: string
    label: rhpdsurl
</code></pre>
INJECTOR CONFIGURATION:
<pre class="line-number language-yaml"><code>
extra_vars:
  rhpdspass: '{{password}}'
  rhpdsurl: '{{url}}'
  rhpdsuser: '{{username}}'
</code></pre>

If you want to have this script create/update RHPDS AWS sandbox API KEY and SECRET you will need to Create Ansible Tower Creds

<B>Template Extravar Examples  </B>
<pre class="line-number language-yaml"><code>
---
org: Random Org
catalogitem : 30000000000080
notes: 'Customer Activity - Proof of Concept provisioned by AnsibleAPI'
rhpdsorder: '{ "action": "order", "resource": { "href":
  "https://rhpds.redhat.com/api/v3.0.0/service_templates/30000000000840",
  "check" : "t",
  "notes" : " {{notes}} ",
  "expiration" : "7"
  } }'
  </code></pre>
  
  <B>Template setup example - Notice added Custom Creds for RHPDS and Ansible Tower - NOTE if you dont add Ansible Tower creds the Creds of AWS_RHPDS_API will not be created or updated!  </B>
  
  ![image](https://user-images.githubusercontent.com/17077661/120363581-2a5ac300-c2c1-11eb-8fc2-1a5c54dab9f6.png)



