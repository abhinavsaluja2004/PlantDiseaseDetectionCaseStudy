---
title: Artifact Binary Provenance Abhinav
weight: 1
tldr: Every software running production has known provenance
rationale: High security environment require a tamper-proof identity scheme. The use of Content Addressable Storage mechanisms ensures that if software changes it will have a different identity.
risks:
 - supply-chain
level: 1
---

# {{% param "title" %}}
{{< area_head >}}


## Background
To define software identity, you use the cryptographic hash of the software itself. We use the SHA256 digest of the sofware binary.

This means that if a single byte in the software changes it will have a different identity.

{{< figure src="/images/binary-provenance.svg" alt="Binary Provenance" >}}

## What evidence to record

- The SHA256 of the artifact (docker image, zip file, ...)
- A human readable name
- The git commit that produced it
- The git repository state (clean, unstaged files, ...)
- A url to the build log
- The build environment information
- The software bill of materials

## Alternative identification of artifacts

It can be helpful to use human-friendly identites in CI displays, filenames, and docker image tags.  Some examples could be semver, or git source commits.

These are very useful ways for humans to navigate identity through version control and CI systems. However, since they are fallible, they cannot be used to identify software in the security and compliance areas.

Use labels for humans and SHAs for machines.

## Further reading
* [How to secure your software supply chain with artifact binary provenance](https://www.kosli.com/blog/how-to-secure-your-software-supply-chain-with-artifact-binary-provenance/)
