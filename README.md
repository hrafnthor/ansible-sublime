# ansible-sublime
An Ansible role for installing Sublime 


#### 

```yaml
sublime:
    signing:		
        path:		(String) Path to the repository pgp key. required in [signing] block.
        force:		(boolean) Indicates if the key should be forcefully updated.
    priority:		(boolean) Indicates if the repository should have highest priority
```