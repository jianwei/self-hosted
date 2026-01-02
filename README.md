# Self-Hosted Sentry

[Sentry](https://sentry.io/), feature-complete and packaged up for low-volume deployments and proofs-of-concept.

Documentation [here](https://develop.sentry.dev/self-hosted/).

## 修改说明

**文件**: `sentry\sentry.conf.py`

```python
CSRF_TRUSTED_ORIGINS = ["https://example.com", "http://127.0.0.1:9000", "http://be.mmszxc.xin:63588"]
```

