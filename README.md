# instabox-keepalive

Keeps the Instabox VMs behind the Amp orb providers awake by renewing their
activity leases from GitHub Actions every 5 minutes.

`keepalive.sh` is vendored from
[pingmike2/instabox-keepalive](https://github.com/pingmike2/instabox-keepalive)
(sha256 `db86c41d6ee95f3b132e4468a587b000626fe1ba9f971d24fd4443a0242ea458`).

## Setup

Add the Instabox API keys as one comma-separated repository secret:

```sh
gh secret set INSTABOX_API_KEY --body "ibk_key1,ibk_key2,ibk_key3"
```

The workflow runs `sh ./keepalive.sh --once` with `INSTABOX_AUTO_RESUME=1`,
so it renews every machine visible to those keys and resumes any machine that
was paused or stopped.
