---
uid: Cube_Feature_Release_10.5.5
---

# DataMiner Cube Feature Release 10.5.5 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
>
> - For release notes related to the general DataMiner release, see [General Feature Release 10.5.5](xref:General_Feature_Release_10.5.5).
> - For release notes related to the DataMiner web applications, see [DataMiner web apps Feature Release 10.5.5](xref:Web_apps_Feature_Release_10.5.5).

## Highlights

*No highlights have been selected yet.*

## New features

*No new features have been added yet.*

## Changes

### Enhancements

#### DataMiner Cube desktop app: Enhanced configuration file management and revised drag-and-drop functionality [ID 41203]

<!-- MR 10.4.0 [CU14] / 10.5.0 [CU2] - FR 10.5.5 -->

In the DataMiner Cube desktop app, a number of enhancements have been made with regard to configuration file management.

Also, the drag-and-drop functionality has been revised. For example, it is now possible to re-order tile groups and to remove tiles by dragging them onto the recycle bin.

#### Alarm Console: Multivariate pattern suggestion events will now be grouped into a single incident [ID 42287]

<!-- MR 10.4.0 [CU14] / 10.5.0 [CU2] - FR 10.5.5 -->

When a multivariate pattern is detected in new trend data, suggestion events are generated for every parameter in the linked pattern.

From now on, those suggestion events will be grouped into a single incident, which will be shown as a single line in both the *Suggestion events* tab and the *Patterns* tab of the Alarm Console.

#### Alarm templates: Warning message will now appear when you try to enable smart baselines for a history set parameter [ID 42326]

<!-- MR 10.4.0 [CU14] / 10.5.0 [CU2] - FR 10.5.5 -->

When you enable smart baselines for a parameter that has its `historySet` option set to true in the connector in question, from now on, a warning message will appear, saying that historySet functionality is incompatible with smart baselines.

> [!NOTE]
> Although, in the UI, the smart baseline option will be enabled for the parameter in question, the option will have no effect as long as the parameter has its `historySet` option set to true in the connector.

#### System Center - System settings: 'Time to live' section will no longer be available when Cube is connected to a DMS using STaaS [ID 42333]

<!-- MR 10.4.0 [CU14] / 10.5.0 [CU2] - FR 10.5.5 -->

In *System Center > System settings*, the *Time to live* section will no longer be available when Cube is connected to a DMS using STaaS.

### Fixes

*No fixes have been added yet.*
