# Git Setup Checklist

## Start with a Secure Foundation:

Begin by installing Git from official sources or trusted package managers. Always use the latest stable version to benefit from security patches and updates. This ensures that your development environment is fortified against known vulnerabilities.

## Use SSH for Secure Repository Access:

When interacting with remote repositories, prefer using SSH (Secure Shell) over HTTPS. SSH provides a secure communication channel between your machine and the remote repository.

## Implement Two-Factor Authentication (2FA):

For platforms supporting it, enable Two-Factor Authentication. Adding an extra layer of verification significantly enhances the security of your account. Services like GitHub, GitLab, and Bitbucket provide straightforward ways to enable 2FA, adding an additional step during authentication.

## Configure Git Identity:

Set up your Git identity with your name and email address. This information is embedded in your commits, providing accountability. Use the following commands to configure your identity:

```zsh
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## Enable GPG for Commit Signing:

Signing your commits with GPG (GNU Privacy Guard) keys ensures the integrity of your code.
Follow this link to enable commit signing: [GithubDoc Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)

## Regularly Review Git Configurations:

Periodically review your Git configurations, both global and local, to ensure only necessary settings are in place. Remove any unused aliases, custom scripts, or configurations that may pose security risks.

## Implement Branch Protection:

If working in a collaborative environment, set up branch protection rules. This adds an extra layer of control, preventing accidental or unauthorized changes to critical branches. Platforms like GitHub and GitLab allow you to configure branch protection settings.

## Conclusion:

By following these developer security best practices for Git setup, you build a secure foundation for your codebase. These measures not only protect your code from unauthorized access and tampering but also contribute to a culture of secure and accountable software development. Remember, security is a collaborative effort, and every developer plays a crucial role in building and maintaining a robust codebase.
