## Changelog NETN-SE

### v1.0 - Developed by MSG-163 for NETN FOM v3.0



### v2.0 - Developed by MSG-191 for NATO FOM v4.0

* Major harmonization with RPR-FOM SE module
* Removed datatype GeoLocationReferenceVariant
* Removed object class `Facility`
** `Facility` attribute `UniqueId` moved to NETN-BASE `HLAobjectRoot`
** `Facility` attribute `LocationReference` replaced by similar RPR-SE attributes on relevant subclasses of `EnvironmentObject`
** `Facility` attribute `PercentComplete` replaced by similar RPR-SE attribute on relevant subclasses of `EnvironmentObject`
** `Facility` attribute `ForceId` and `ObjectType` replaced by similar RPR-SE attribute on `EnvironmentObject` object class
** `Facility` attribute `Name`, `SymbolId`, `DamageState`, `Comment` and `Status` moved to `EnvironmentObject
* Attribute `HostObject` added to `EnvironmentObject` object class.
* Changed superclass of object class `Checkpoint` to `PointObject`
* Replaced object class `SE_GeoObject`, `Location`, `Path` and `Region` and associated attributes with `PointObject`, `LinearObject` and `ArealObject` object classes
* Added attribute `Radius` to `PointObject` object class
* Added attribute `Points` to `LinearObject` object class
* Added attribute `Delayime` to `Checkpoint` object class
* Added object class `ArealBreach` and `Minefield` as subclasses of `ArealObject` object class
* Added attribute `Density` to `Minefield` object class

