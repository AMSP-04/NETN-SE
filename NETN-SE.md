# NETN-SE
Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

The NATO Education and Training Network Synthetic Environment Module (NETN-SE) is a specification of how to represent generic synthetic environment elements such as geographical Locations, Paths and Regions in a federated distributed simulation. It also specifices how to represent Facility object that represent some function or capability associated with a geographic locations or a specific entity.

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module is used to specify how data is represented and exchanged in the federation. The NETN-ORG FOM module is available as an XML file for use in HLA based federations.

### Purpose

The NETN-SE FOM Module provides a common standard interface for representing persistent abstact geographical objects that can be (re-)used and referenced for specifying locations, paths, and regions. The module also include the representation of facilities with a function or capability to perform activities.

### Scope

The current version of the NETN-SE is limited to:

- Representation of Checkpoint Facilities
- Representation of specific geographical Locations, Paths and Regions

## Object Classes

### Facility

The `SE_Facility` object class is a base class for all types of facilities. In the current version of NETN-SE the only Facility represented is a `Checkpoint` facility.

|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Pre-defined or generated unique identifier of the object instance.|
|LocationReference|**Required.** A reference that identifies a geographical location directly or indirectly by reference to simulated object.|
|Name|**Optional.** Name of the facility.|
|SymbolId|**Optional.** A symbol identifier represented as a string. The symbol standard used is indicated using an URI notation (uri:xxxxxxxxxx). The following uri should be used for common symbology standards app6b, app6b, app6c, app6c, 2525b, 2525c, 2525d. If not provided the symbol standard used is undefined.|
|Status|**Optional.** Specifies if the facility is active (operational) or not. Default value is 1 (Active).|
|ObjectType|**Optional.** Specifying the domain, the kind and the specific identification of the environment object.|
|ForceId|**Optional.** The force that operates the Facility. Default is 0 (Other).|
|PercentComplete|**Optional.** Describes the level of completness during establishment/building of facility expressed in percent [0-100]. Default is 100%.|
|DamageState|**Optional.** The damage state on the Facility. Default value is 0 (NoDamage).|
|Comment|**Optional.** A descriptive text comment.|

#### Checkpoint

A `CheckPoint` defines a location where simulated aggregate and physical entities should stop and wait a specified time before continuing on their route.
If the checkpoint is currently in operation the status attribute should be set to true. A system simulating movement of physical or aggregate entities can be either directly affected by the checkpoint by subscribing to its state or indirectly by receiving an NETN-ETR `Wait` task.  

<img src=./images/se-checkpoint.png>

**Figure: Checkpoint Facility**

|Attribtue|Description|
|---|---|
|DelayTime|**Required.** The time that an entity shall wait at the checkpoint before passing. This is a nominal value, federates can use this for modifing delay time for different types if entities, e.g add or subtract a value or multiply with a type depending factor.|


### GeoObject

The `SE_GeoObject` is a representation of geographically associated locations, paths, and regions with or without a defined name. E.g. a harbour may be represented as a Location with a specific name, a commonly used route can be represented as a named path and a region can be represented as an specific geographic are and reused as an object instance in the simulation. All `SE_GeoObject` are defined relative to the earth surface using a geodetic reference.

<img src=./images/se-objectclasses.png>

**Figure: GeoObject classes**

#### Location
|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Unique identifier for the GeoObject.|
|Name|**Optional:** Name of the GeoObject, e.g. Location name, Road name etc.|
|Point|**Required:** A geographical point in lat, lon and altitude above mean sea level.|


#### Path
|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Unique identifier for the GeoObject.|
|Name|**Optional:** Name of the GeoObject, e.g. Location name, Road name etc.|
|Points|**Required:** A path with at least 2 points expressed as GeodeticPoints.|

#### Region
|Attribtue|Description|
|---|---|
|UniqueId|**Required.** Unique identifier for the GeoObject.|
|Name|**Optional:** Name of the GeoObject, e.g. Location name, Road name etc.|
|Area|**Required:** Defines the area, either as a geodetic polygon,circle or a quadrangle.|





