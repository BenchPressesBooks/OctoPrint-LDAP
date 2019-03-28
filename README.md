OctoPrint LDAP auth Plugin
=========================

This plugin allow users to be authenticated using an LDAP server.

#### Details

When you try to login, OctoPrint will search for the user in its local database (users.yaml)
- If the user is found, check if this user also exists in LDAP
- If user exists in LDAP, use LDAP bind() to check login / password
- If they don't exist in LDAP, use native password system to check it

======================================

- If it did not found a user in the local database, try to connect directly using LDAP
- If login with LDAP succeeds, a new local user is added with role "user" and a random password (password should never be used)
- User is then authenticated and authorized

======================================

- An admin (default user for exemple), could change a user permissions or account state.
- Password of LDAP users can't be changed

#### Configuration

You could configure LDAP server in plugin config, or manually in config.yaml

```
accessControl:
  ldap_uri: ldaps://ldap.server.com/
  ldap_tls_reqcert: demand
  ldap_search_base: dc=server,dc=com
  groups: TheGroupName
```

#### Groups
- You can list multiple groups via comma seperation: Group1, Group2, Group3. 
- Leaving blank will skip a group check.

#### Installation

You can install it using ```pip install https://github.com/BenchPressesBooks/OctoPrint-LDAP/archive/master.zip```

Or with plugin manager in OctoPrint using the zip location.
