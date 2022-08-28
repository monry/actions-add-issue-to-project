# Add GitHub Issues to GitHub Projects

Add issue to project.

# Usage

## Specify parameters without id

```yaml
- uses: monry/actions-add-issue-to-project@v2
  with:
    # Personal Access Token that with `repo`, `org:read` and `org:write` are granted.
    github-token: ${{ secrets.PAT_PROJECT_V2 }}
    project-owner: 'monry'
    project-number: 1
    issue-repository: 'monry/awesome-repository'
    issue-number: 100
```

## Specify parameters with id

```yaml
- uses: monry/actions-add-issue-to-project@v2
  with:
    # Personal Access Token that with `repo`, `org:read` and `org:write` are granted.
    github-token: ${{ secrets.PAT_PROJECT_V2 }}
    project-id: 'PVT_xxxxxxxxxxxxxx'
    issue-id: ${{ github.event.issue.node_id }}
```

# Inputs

## `github-token`

This action requires Personal Access Token that `repo`, `org:read` and `org:write` are granted.

For security purposes, it is recommended to register Personal Access Token as Secrets.

## `project-id`

Node ID of project.

This value can obtain from [monry/actions-get-project-id@v2](https://github.com/marketplace/actions/get-project-id).<br />
See also: [monry/actions-get-project-id](https://github.com/monry/actions-get-project-id) repos.

## `project-owner`

Owner name of project.

Owner name refers to the user name or the organization name.

**NOTICE** This value is required if `project-id` is not specified.

## `project-number`

Project number.

The project number is the number shown in the URL or list of projects.

**NOTICE** This value is required if `project-id` is not specified.

## `issue-id`

Node ID of issue.

This value can obtain from `github.event.issue.node_id` if triggered by `on: issues`, or obtain from [monry/actions-get-issue-id@v1](https://github.com/marketplace/actions/get-issue-id).<br />
See also: [monry/actions-get-issue-id](https://github.com/monry/actions-get-issue-id) repos.

## `issue-repository`

Repository name of issue with owner name.

**NOTICE** This value is required if `issue-id` is not specified.

## `issue-number`

Number of issue.

**NOTICE** This value is required if `issue-id` is not specified.

# Outputs

## `added-project-item-id`

Added Project Item Id stores into output variable named `added-project-item-id`.

```yaml
- uses: monry/actions-add-issue-to-project@v2
  id: add-issue-to-project # requires `id` to refer output values with after steps
  with:
    github-token: ${{ secrets.PAT_PROJECT_V2 }}
    project-owner: 'monry'
    project-number: 1
    issue-repository: 'monry/awesome-repository'
    issue-number: 100
- run: |
    echo '${{ steps.add-issue-to-project.outputs.added-project-item-id }}'
```

## `error`

Set error message if some error occured.
