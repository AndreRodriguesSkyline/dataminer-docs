---
uid: SwarmingFAQ
---

# Frequently asked questions

## Can I swarm X/Y/Z?

Swarming will gradually become available for more and more functionality in DataMiner.

In the initial version released in DataMiner 10.5.1, only basic elements are supported.

For a list of upcoming features, see [Upcoming features](xref:Swarming#upcoming-features).

## Does the ID of an element change when it is swarmed?

No, the identifier (DataMiner ID/element ID) of an element that is swarmed stays the same. You can find this identifier by right-clicking an element in the Cube Surveyor and selecting *Properties*:

![Element ID in Cube](~/user-guide/images/Swarming_FAQ_DataMinerID.png)

The **DataMiner ID** part of the identifier does not refer to the Agent hosting the element but to the Agent where the element was originally created. Combined with the element ID part, it creates a unique identifier for an element throughout the DMS.

Each element also stores where it is hosted, and that **Host ID** field is updated when the element is swarmed. To find this field, open the parent view of the element in DataMiner Cube, and scroll to the right in the list of elements until you see the *HOST ID* and *DATAMINER* column for the element. For example, here you can see these columns after the column order has been adjusted to show them side by side with the *NAME* and *ID*:

![Hosting Agent in Cube](~/user-guide/images/Swarming_FAQ_HostingAgentCube.png)

To find out which Agent is hosting an element using code, use the *HostingAgentID* property.

## Can I block an element from being swarmed?

This feature is currently not yet available but will become available soon.

## What happens with my Elements folder on disk?

When swarming is not enabled, the configuration of an element is stored in an [XML file on the DataMiner server](xref:Elements1).

In order for Swarming to work, every Agent needs to be able to access all data of an element, including its configuration. For this reason, the configuration is moved to the shared database instead. This data migration happens automatically during DataMiner startup after you enable Swarming.

## How does the element license work?

Enabling Swarming does not affect the licensing for elements.

If you have a perpetual-use license, there is a limit to how many elements can be added per Agent. If you swarm an element, and this causes the element limit of an Agent to be exceeded, the element will not start up, and the Swarming request will return as a failure. This is similar to the behavior when you go over the element limit by manually creating a new element.

## How do I know why my element is not swarmable?

The only way to see this at present is to attempt to swarm the element via the Automation API and look at the error message.

## How do Agents know which elements to host when starting up?

This info is stored in the database together with the element. Each element has a field storing its current host. When an element swarms to another Agent, this field is updated.
