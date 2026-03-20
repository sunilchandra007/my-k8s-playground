# User, group, access
```bash
# current user - Who am I?
id

# What users exist?
cat /etc/passwd

# What groups exist?
cat /etc/group

# Find directories owned by a user?
find /path -type d -user 1000 2>/dev/null
```
# text search
```bash
grep -Rni -C 3 "search-text" /path 2>/dev/null
```
