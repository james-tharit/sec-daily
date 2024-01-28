# Multiple Git configs Setup

> Git has a conditional includes section. This allows you to override your configuration in each unique directory.

For example, you could keep all your work projects inside your `~/work_projects`` directory and set your work email as the committer email for projects under this directory.

### Let's see how to do this.

Add an includeIf statement to your .gitconfig:

```toml
[includeIf "gitdir:~/work_projects"]
	path = ~/.gitconfig_work
```

- replace "~/work_projects" with your desired directory
- replace "~/.gitconfig_work" with your custom configuration file

The .gitconfig_work will be just like your .gitconfig, but will store your GitHub work account instead of the default one.

```toml
[user]
	name = your-github-work-username
	email = your-github-work-email
[core]
	sshCommand = ssh -i ~/.ssh/id_work_rsa
```

That’s it! Now all the repositories inside ~/work_projects will use your work email and work SSH.
