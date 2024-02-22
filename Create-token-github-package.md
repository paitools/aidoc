To obtain the API key for GitHub Packages, you will be using the GitHub Personal Access Token, specifically designed for use with GitHub Actions. Follow these steps to generate and use the API key:

### Generate Personal Access Token:

1. Go to your GitHub account settings.
2. Navigate to the "Developer settings" > "Personal access tokens" section, or directly visit: [https://github.com/settings/tokens](https://github.com/settings/tokens).
3. Click on the "Generate new token" button.
4. Give your token a descriptive name and select the appropriate scopes. For GitHub Packages, you'll need to select at least the `write:packages` scope.
5. Click on the "Generate token" button at the bottom of the page.
6. Copy and Store Your Token:
    - After generating the token, GitHub will display it only once. Copy the token and store it securely.
    - Be cautious with this token as it provides access to your GitHub account and repositories.

### Add the Token to Your GitHub Repository:

1. In your GitHub repository, go to the "Settings" tab.
2. Select "Secrets" from the left sidebar.
3. Click on the "New repository secret" button.
4. Name your secret (for example, `GITHUB_TOKEN`) and paste the token you generated in the previous step.
5. Click "Add secret" to save it.

### Use the Token in Your GitHub Actions Workflow:

- In your GitHub Actions workflow YAML file, you can reference the token using the `${{ secrets.GITHUB_TOKEN }}` syntax.
- For example, in the `nuget push` command, you would use `--api-key ${{ secrets.GITHUB_TOKEN }}` to provide the token as the API key.

Here's an example of how you might use the token in your GitHub Actions workflow YAML file:

```yaml
- name: Publish to GitHub Packages
  run: |
    dotnet nuget push YourLibrary.*.nupkg --source {URL of your github packages} --api-key ${{secrets.GITHUB_TOKEN}}
```
For example, dotnet nuget push .\out\KeywordSearch.*.nupkg -s https://nuget.pkg.github.com/paitools/index.json --api-key ${{secrets.GITHUB_TOKEN}}
