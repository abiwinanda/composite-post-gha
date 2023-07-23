# Composite Post GitHub Action

Sample GHA workflow that demonstrates how to create a composite action that incorporate post steps.

The underlying composite action (`.github/actions/cache`) is using another composite action that allows it to create post steps.

```yaml
name: Cache

description: "Dummy action to perform cache."

runs:
  using: "composite"
  steps:
    - name: Cache
      uses: ./.github/actions/with-post-steps
      with:
        main: echo "Restoring cache..."
        post: echo "Rebuilding cache..."
```

Notice that multiple command can be used in the `main:` and `post:`

```yaml
name: Cache

description: "Dummy action to perform cache."

runs:
  using: "composite"
  steps:
    - name: Cache
      uses: ./.github/actions/with-post-steps
      with:
        main: |
          echo "do something"
          echo "do something else"
          ...
        post: |
          echo "do something"
          echo "do something else"
          ...
```

# Reference

- https://github.com/actions/runner/issues/1478#issuecomment-975703207
