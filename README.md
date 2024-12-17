# GitHub App Authentication

This repository contains a script to generate a GitHub App token with a specific repository access.

## Prerequisites

- PowerShell 5.1 or later
- GitHub App credentials (App ID, Private Key file)
- GitHub repository name

## Instructions

1. Clone the repository:

    ```powershell
    git clone https://github.com/martins-vds/github-app-authentication.git
    cd github-app-authentication
    ```

2. Open PowerShell and navigate to the repository directory.

3. Run the script `generate-token.ps1` with the required parameters:

    ```powershell
    .\generate-token.ps1 -AppClientId <YourAppId> -AppPrivateKeyPath <PathToYourPrivateKey> -Repository <YourRepositoryName>
    ```

    - Replace `<YourAppId>` with your GitHub App ID.
    - Replace `<PathToYourPrivateKey>` with the path to your GitHub App's private key file.
    - Replace `<YourRepositoryName>` with the name of your GitHub repository. The repository name must match the pattern `owner/repo` (e.g., `octocat/hello-world`).

4. The script will output the generated token which you can use to authenticate with the GitHub API.

## Example

- Generate a token for a GitHub App with ID `12345`, private key file `private-key.pem` to clone the repository `octocat/hello-world` into a local directory `hello-world`:

    ```powershell
    $repo=octocat/hello-world
    $dir=hello-world
    $token=.\generate-token.ps1 -AppClientId 12345 -AppPrivateKeyPath .\private-key.pem -Repository $repo
    git clone https://x-access-token:$($token)@github.com/$($repo).git $dir
    ```
