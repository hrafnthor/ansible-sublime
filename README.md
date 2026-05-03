# ansible-sublime

An Ansible role for installing Sublime


####

All values are optional unless otherwise indicated.

```yaml
sublime:
  remove:   [boolean] Indicates if the package should be removed.
  signing:
    path:   [string]  Path to the repository pgp key. required in [signing] block.
    force:  [boolean] Indicates if the key should be forcefully updated.
  priority: [boolean] Indicates if the repository should have highest priority
```