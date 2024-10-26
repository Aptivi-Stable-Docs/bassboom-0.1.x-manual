---
description: How to install BassBoom to your PC
icon: compact-disc
---

# Installing BassBoom

BassBoom can be installed on all the supported platforms. The installation steps are straightforward, but must be followed in order to ensure that the kernel starts right.

Depending on your platform, the amount of disk space taken by BassBoom and its runtime dependencies might vary. Select your platform below and follow the steps.

{% content-ref url="windows.md" %}
[windows.md](windows.md)
{% endcontent-ref %}

{% content-ref url="linux.md" %}
[linux.md](linux.md)
{% endcontent-ref %}

{% content-ref url="android.md" %}
[android.md](android.md)
{% endcontent-ref %}

## Verifying intregrity <a href="#verifying-intregrity" id="verifying-intregrity"></a>

You can verify the integrity of all the BassBoom release assets using the GitHub Attestations feature.

GitHub have recently introduced a new feature that allows you to verify a binary artifact that a workflow has generated, called the [Attestations](https://github.blog/2024-05-02-introducing-artifact-attestations-now-in-public-beta/). To verify your download, once you've downloaded one of the BassBoom zip files, follow these steps:

1. Install [GH CLI 2.49.0](https://github.com/cli/cli/releases/tag/v2.49.0) or higher.
2. Sign in to your GitHub account using `gh auth login`.
3. Run this command: `gh attestation verify <version>-cli.zip --owner Aptivi`, where `<version>` is a version of Nitrocid that you've downloaded.

If everything is OK, you should see the below message, such as one for 0.1.3:

```
Loaded digest sha256:9ada4db3af9bc9579480e8177211f6ec261adc959641f8a30a47468f0c42969c for file://0.1.3-cli.zip
Loaded 1 attestation from GitHub API
✓ Verification succeeded!

sha256:9ada4db3af9bc9579480e8177211f6ec261adc959641f8a30a47468f0c42969c was attested by:
REPO             PREDICATE_TYPE                  WORKFLOW
Aptivi/BassBoom  https://slsa.dev/provenance/v1  .github/workflows/prepdraft.yml@refs/tags/v0.1.3
```

{% hint style="info" %}
If you've seen this error message:

```
Loaded digest sha256:78fc7b18c2e5e2753934652d294456d11d8dadad6f638dedc31513c4570587a1 for file://0.1.0.10-bin-lite.zip
✗ Loading attestations from GitHub API failed

Error: failed to fetch attestations from Aptivi: HTTP 404: Not Found (https://api.github.com/orgs/Aptivi/attestations/sha256:78fc7b18c2e5e2753934652d294456d11d8dadad6f638dedc31513c4570587a1?per_page=30)
```

Then, your download is corrupt.
{% endhint %}
