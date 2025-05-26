# Create NuGet.Config Action

This GitHub Action generates a `NuGet.Config` file with customizable parameters for file path, repository URL, username, and password. It provides default values which can be overridden with inputs.

## Inputs

- `file-path` (optional): The path where the `NuGet.Config` file will be created. Defaults to `NuGet.Config`.

- `repository-url` (optional): The URL of the NuGet package repository. Defaults to `https://nuget.pkg.github.com/${{ github.repository_owner }}/index.json`.

- `username` (optional): The username for the private repository. Defaults to `${{ github.actor }}`.

- `password` (optional): The password or token for the private repository. 

## Usage

To use this action in your workflows, include it as a step within your job. You can optionally specify inputs to customize the behavior.

### Example Workflow

```yaml
name: Generate NuGet.Config

on:
  push:
    branches:
      - main

jobs:
  create-nuget-config:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Create NuGet.Config
        uses: Rebel028/create-nuget-config-action@master
        with:
          file-path: 'custom/NuGet.Config'
          repository-url: 'https://custom.repo.url/index.json'
          username: 'custom-username'
          password: '${{ secrets.GITHUB_TOKEN }}'
```

### Default Usage

If no inputs are provided, the action uses the following defaults:

- `file-path`: `NuGet.Config`
- `repository-url`: `https://nuget.pkg.github.com/${{ github.repository_owner }}/index.json`
- `username`: `${{ github.actor }}`

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

If you encounter any issues or have questions, please open an issue in this repository.