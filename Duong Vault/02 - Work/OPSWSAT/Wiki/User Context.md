- **Document**: [Categorization of different behaviors in patching for per-user and per-machine - OESIS AND Vulnerability - Confluence (atlassian.net)](https://opswat.atlassian.net/wiki/spaces/OES/pages/2867626936/Categorization+of+different+behaviors+in+patching+for+per-user+and+per-machine)
- **Test cases:** [User context - OESIS AND Vulnerability - Confluence (atlassian.net)](https://opswat.atlassian.net/wiki/spaces/OES/pages/3212804189/User+context)

```cpp
// This is cu_install_type field
enum UserContextPreference
{
    DEFAULT = 0,
    ALL_USER_PREFERRED = 1, // Priority to fresh install for all-user when no base installed
    CURRENT_USER_PREFERRED = 2, //Priority to fresh install for current-user when no base installed
    CURRENT_USER_ONLY = 3 // current-user only
};

// au_install_param_pattern: addtion to install for alluser
// cu_install_param_pattern: addtion to install for current user
```