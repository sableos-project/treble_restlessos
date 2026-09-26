# SableOS Treble / RestlessOS tracking policy

Status: **tracking policy — no release artifact claim**

This repository is the SableOS fork of `cawilliamson/treble_restlessos` used for
Treble portability research and future reviewed Sable Treble patchsets.

It is not the first Titan 2 N0 boot dependency. Titan 2 N0_A16 starts from a
clean AOSP16 GSI substrate; this fork is a reference and future fork line.

## Repository role

```text
REPOSITORY=sableos-project/treble_restlessos
UPSTREAM=cawilliamson/treble_restlessos
ROLE=UPSTREAM_TRACKING_AND_SABLE_TREBLE_PATCHSET
FIRST_TITAN2_SUBSTRATE=AOSP16_CLEAN_GSI
RESTLESSOS_FIRST_BOOT_DEPENDENCY=NO
```

This repository may eventually hold reviewed Sable common Treble changes for
MediaTek/Unihertz portability, but it must not become an implicit source of
release artifacts.

## Branch model

```text
upstream/android-16.2
upstream/android-17.0
sable/android-16.2
sable/android-17.0
sable/titan2-n0-a16
```

### `upstream/*`

`upstream/*` branches are fast-forward mirrors of `cawilliamson/treble_restlessos`.
They must not contain Sable-specific commits.

### `sable/android-*`

`sable/android-*` branches are reviewed Sable common Treble patch branches.
They may diverge from upstream only through explicit PRs that explain:

```text
UPSTREAM_BASE=<exact upstream branch + commit>
SABLE_CHANGE_REASON=<compatibility/security/product reason>
DEVICE_SCOPE=<common|titan2|titan2-elite|q27|other>
RISK=<known compatibility/security risk>
ROLLBACK=<how to revert or disable the change>
```

### `sable/titan2-n0-a16`

`sable/titan2-n0-a16` is a temporary Titan 2 Android 16 experiment branch. It may
be used for comparison and later patch extraction, but it is not a release
composition source until `platform_manifest` pins an exact commit and the build
system records a real artifact hash.

## Release and artifact rules

- No prebuilt RestlessOS image is a SableOS release artifact.
- No GrapheneOS or RestlessOS branding/security claim is inherited by SableOS.
- Mutable branch names are not release provenance.
- `platform_manifest` must pin exact commits before any Sable build consumes this repository.
- `build` must record source identity, artifact identity and verification outputs.
- Device repositories own device-specific stock/vendor basis and deployment gates.

## Prohibited content

Do not commit:

- stock firmware or OTA packages;
- partition images or dumps;
- device serials, IMEI/MEID/ICCID or other private identifiers;
- production signing keys or credentials;
- generated release images unless explicitly authorized by the release policy.

## Titan 2 current status

```text
TITAN2_RELEASE_ID=N0_A16
FIRST_SUBSTRATE=AOSP16_CLEAN_GSI
RESTLESSOS_ROLE=REFERENCE_AND_FUTURE_FORK
RESTLESSOS_FIRST_BOOT_DEPENDENCY=NO
FIRST_SABLE_ARTIFACT=ABSENT
FIRST_SABLE_BOOT=NOT_RUN
PUBLIC_FLASH=NO
```
