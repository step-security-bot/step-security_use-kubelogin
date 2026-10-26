[![StepSecurity Maintained Action](https://raw.githubusercontent.com/step-security/maintained-actions-assets/main/assets/maintained-action-banner.png)](https://docs.stepsecurity.io/actions/stepsecurity-maintained-actions)

# step-security/use-kubelogin

This action helps you to setup [kubelogin][] in your GitHub Actions workflow.

## Action Inputs

| Name | Description | Default | Example |
|:--:|--|--|--|
| `kubelogin-version` (optional) | The version of kubelogin to use. Please see the following section [kubelogin version](#kubelogin-version) for details. | `latest` | `v0.0.24` |
| `skip-cache` (optional) | Skip discovering the kubelogin from cache. By setting this to true will force to download the kubelogin from GitHub release. | `false` | `true` | 

## Usage Examples

### Basic

```yaml
- uses: step-security/use-kubelogin@v1
  with:
    kubelogin-version: 'v0.0.24'
```

### Use Latest Version

> **NOTE**
> We recommend to use a specific version of kubelogin to have consistent behavior.

```yaml
- uses: step-security/use-kubelogin@v1
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  with:
    kubelogin-version: 'latest'
```

### Skip Cache

> **NOTE**
> This option is designed for testing purpose.

```yaml
- uses: step-security/use-kubelogin@v1
  with:
    kubelogin-version: 'v0.0.24'
    skip-cache: 'true'
```

## kubelogin version

If the `kubelogin-version` is not set, or is one of `latest` or `*`, the action will try to use the latest version of kubelogin.
However, due to the GitHub API rate limiting settings, this action requires to pass in the `GITHUB_TOKEN` to the environment variable. If this environment variable is not set, we will see error similar to the following:

```
Run step-security/use-kubelogin@{version}
/home/runner/work/_actions/step-security/use-kubelogin/{version}/lib/index.js:14812
            throw new Error('GITHUB_TOKEN is not set, unable to resolve the latest version of kubelogin');
```

> **NOTE**
> To ensure consistent behavior, it is recommended to specify the version of kubelogin to use. We can find the full list of available versions at [kubelogin releases][].

[kubelogin]: https://github.com/Azure/kubelogin
[kubelogin releases]: https://github.com/Azure/kubelogin/releases

## LICENSE

MIT