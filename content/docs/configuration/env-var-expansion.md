---
title: Environment Variable Expansion
---

Dex supports expanding environment variables in the configuration file. This allows you to use environment variables to configure Dex, which can be useful for security and for managing different environments.

To enable this feature, ensure the `DEX_EXPAND_ENV` environment variable is either unset, set to a "truthy" value (e.g., "1", "true", "TRUE"), or any unrecognized value. To disable this feature, set `DEX_EXPAND_ENV` to a "falsy" value (e.g., "0", "false", "FALSE").

Expansion uses Go's `os.ExpandEnv`, which supports the `$VAR` and `${VAR}` syntax.

## Example

```yaml
storage:
  type: postgres
  config:
    host: '$DEX_FOO_POSTGRES_HOST'
    password: '$DEX_FOO_POSTGRES_PASSWORD'
```

If `DEX_EXPAND_ENV` is enabled and the corresponding environment variables are set, Dex will substitute their values at runtime.
