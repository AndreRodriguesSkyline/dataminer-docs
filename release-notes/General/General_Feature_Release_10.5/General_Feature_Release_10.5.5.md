---
uid: General_Feature_Release_10.5.5
---

# General Feature Release 10.5.5 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!IMPORTANT]
>
> Before you upgrade to this DataMiner version, make sure **version 14.40.33816** or higher of the **Microsoft Visual C++ x86/x64 redistributables** is installed. Otherwise, the upgrade will trigger an **automatic reboot** of the DMA in order to complete the installation.
>
> The latest version of the redistributables can be downloaded from the [Microsoft website](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-microsoft-visual-c-redistributable-version):
>
> - [vc_redist.x86.exe](https://aka.ms/vs/17/release/vc_redist.x86.exe)
> - [vc_redist.x64.exe](https://aka.ms/vs/17/release/vc_redist.x64.exe)

> [!TIP]
>
> - For release notes related to DataMiner Cube, see [DataMiner Cube Feature Release 10.5.5](xref:Cube_Feature_Release_10.5.5).
> - For release notes related to the DataMiner web applications, see [DataMiner web apps Feature Release 10.5.5](xref:Web_apps_Feature_Release_10.5.5).
> - For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

## Highlights

*No highlights have been selected yet.*

## New features

*No new features have been added yet.*

## Changes

### Enhancements

#### Security enhancements [ID 42307]

<!-- 42307: MR 10.4.0 [CU14]/10.5.0 [CU2] - FR 10.5.5 -->

A number of security enhancements have been made.

### Fixes

#### Problem with aggregation alarms on Cassandra Cluster and STaaS [ID 42095]

<!-- MR 10.4.0 [CU14]/10.5.0 [CU2] - FR 10.5.5 -->

Up to now, aggregation alarms would not work as intended on DataMiner Systems using a Cassandra Cluster database or Storage as a Service (STaaS).

#### Mobile Visual Overview: Problem with SLHelper when removing mobile visual overview sessions [ID 42296]

<!-- MR 10.4.0 [CU14]/10.5.0 [CU2] - FR 10.5.5 -->

When mobile visual overview sessions were removed from a DataMiner Agent, in some cases, the SLHelper process could temporarily block other requests.

#### Element card of a DVE or Virtual Function could show incorrect alarm colors [ID 42402]

<!-- MR 10.4.0 [CU14]/10.5.0 [CU2] - FR 10.5.5 -->

In some cases, the `ParameterChangeEvent` or `ParameterTableUpdateEventMessage` for a primary key cell would contain an invalid `InstanceAlarmlevel` or `CellBubbleUpLevel`. As a result, when you opened an element card of a DVE or a Virtual Function, the card pages would show incorrect alarm colors.
