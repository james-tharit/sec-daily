# Managing Multiple Git Accounts on the Same Computer

When working as a consultant on the same computer, you might have two different git accounts—one for your consulting firm and another for your client. It's important to keep these separate to prevent any accidental sharing of client data. One way to achieve this is by using conditional includes in your git configuration.

## Here's how you can set it up:

1. Open your .gitconfig file.
2. Add the following lines at the end:

```toml
[includeIf "gitdir:~/client_projects"]
	path = ~/.gitconfig_client
```

- Replace "~/client_projects" with the directory where you keep your client projects.
- Replace "~/.gitconfig_client" with the custom configuration file for your client.

3. Create a new file named .gitconfig_client with the following content:

```toml
[user]
	name = your-github-client-username
	email = your-github-client-email
[core]
	sshCommand = ssh -i ~/.ssh/client_ssh
```

- Replace "your-github-client-username" and "your-github-client-email" with your client's GitHub username and email.
- If you have a custom SSH key for your client, update the path accordingly.

> Now, any repositories inside the specified directory (~/client_projects) will use your client's email and SSH settings.

This helps avoid accidental commits with the wrong email, ensuring that your client's information is kept separate from your default git configuration.
