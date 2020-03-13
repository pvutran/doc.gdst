---
title: Fishing Event
description: This page covers information about capturing the Fishing / Wild Harvest event.
---

Fishing Events are used to record when products are harvested from the wild. There are different scenarios that can occur. For the most part Fishing Events should be recorded for each unique harvesting that takes place from the ocean. However, we do recognize that limitations in the industry may not allow for that level of granularity when recording Fishing Events. In the case that level of granularity is not possible, then we recommend that Fishing Events be recorded as often as is possible during a fishing trip.

*For events after the Fishing Event, we will be building upon the scenario of Mulitple Harvests and Multiple Fishing Events.*

## Multiple Harvests and Single Fishing Event
This covers when a single large vessel harvested products from multiple locations while on their fishing trip but only wants to record a single fishing event. In this case, we cannot record a single latitude / longitude for the fishing event, and will just list out all the products captured. in this case we won't record a read point, and will just record a catch area.

In this scenario a fishing vessel named **BING Ship** owned by **Bing Fishing Co.** has gone fishing in **FAO Zone 77**. It has gone trawling in multiple locations for **Tuna**. In this scenario the fishing vessel caught **10,000 Kilograms** of Tuna through out it's fishing trip.

```xml
<!-- FISHING EVENT -->
<ObjectEvent>
    <eventTime>2020-01-27T18:00:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>CD42262C-844C-403C-85C5-34728F7FCDA5</eventID>
    </baseExtension>
    <epcList/>
    <action>ADD</action>
    <bizStep>urn:epcglobal:cbv:bizstep:commissioning</bizStep>
    <disposition>urn:epcglobal:cbv:disp:active</disposition>

    <!-- BING Ship -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.47797660-9355-4f8c-8867-c98ee1e8b684</id>
    </bizLocation>

    <extension>
        <quantityList>

            <!-- YELLOW FIN TUNA -->
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT.LOT123</epcClass>
                <quantity>10000.0</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <ilmd>

            <!-- CATCH INFORMATION -->
            <cbvmda:vesselCatchInformationList>
                <cbvmda:vesselCatchInformation>

                    <!-- FAO ZONE 77 -->
                    <cbvmda:catchArea>77</cbvmda:catchArea>

                    <!-- GEAR TYPE: Beam Trawls -->
                    <cbvmda:fishingGearTypeCode>TBB</cbvmda:fishingGearTypeCode>
                </cbvmda:vesselCatchInformation>
            </cbvmda:vesselCatchInformationList>

            <!-- WILD HARVEST -->
            <productionMethodForFishAndSeafoodCode>MARINE_FISHERY</productionMethodForFishAndSeafoodCode>
            
            <cbvmda:harvestStartDate>2020-01-27</cbvmda:harvestStartDate>
            <cbvmda:harvestEndDate>2020-01-27</cbvmda:harvestEndDate>

            <!-- CATCH CERTIFICATE (?) -->
            <cbvmda:certificationList>
                <cbvmda:certification>
                    <gdst:certificateType>urn:gdst:certType:catch_certificate</gdst:certificateType>
                    <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
                    <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
                    <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
                    <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
                </cbvmda:certification>
            </cbvmda:certificationList>
        </ilmd>
    </extension>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Bing Fishing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</cbvmda:informationProvider>
</ObjectEvent>
```

## Multiple Harvests and Multiple Fishing Events
This covers when a vessel harvests products from multiple locations and will record a fishing event for each time they harvested products. In this case, we will record the latitude and longitude for each fishing event.

In this scenario a fishing vessel named **BING Ship** owned by **Bing Fishing Co.** has gone fishing in **FAO Zone 77**. It has gone trawling in multiple locations for **Tuna**. In this scenario the fishing vessel caught **10,000 Kilograms** of Tuna through out it's fishing trip trawling in 4 different locations. Each time the fishing vessel went trawling, it caught **2,500 Kilograms** at each location and recorded a Fishing Event each time with a latitude and longitude for where the trawling occured.

**Fishing Event #1**
```xml
<!-- FISHING EVENT -->
<ObjectEvent>
    <eventTime>2020-01-27T2:00:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>2743D44E-4E20-4237-BA68-1842F3173790</eventID>
    </baseExtension>
    <epcList/>
    <action>ADD</action>
    <bizStep>urn:epcglobal:cbv:bizstep:commissioning</bizStep>
    <disposition>urn:epcglobal:cbv:disp:active</disposition>
    <readPoint>
        <id>geo:38.288338,-124.018110</id>
    </readPoint>

    <!-- BING Ship -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.47797660-9355-4f8c-8867-c98ee1e8b684</id>
    </bizLocation>

    <extension>
        <quantityList>

            <!-- YELLOW FIN TUNA -->
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT.LOT1111</epcClass>
                <quantity>2500.0</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <ilmd>

            <!-- CATCH INFORMATION -->
            <cbvmda:vesselCatchInformationList>
                <cbvmda:vesselCatchInformation>

                    <!-- FAO ZONE 77 -->
                    <cbvmda:catchArea>77</cbvmda:catchArea>

                    <!-- GEAR TYPE: Beam Trawls -->
                    <cbvmda:fishingGearTypeCode>TBB</cbvmda:fishingGearTypeCode>
                </cbvmda:vesselCatchInformation>
            </cbvmda:vesselCatchInformationList>

            <!-- WILD HARVEST -->
            <productionMethodForFishAndSeafoodCode>MARINE_FISHERY</productionMethodForFishAndSeafoodCode>
            
            <cbvmda:harvestStartDate>2020-01-27</cbvmda:harvestStartDate>
            <cbvmda:harvestEndDate>2020-01-27</cbvmda:harvestEndDate>

            <!-- CATCH CERTIFICATE -->
            <cbvmda:certificationList>
                <cbvmda:certification>
                    <gdst:certificateType>urn:gdst:certType:catch_certificate</gdst:certificateType>
                    <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
                    <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
                    <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
                    <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
                </cbvmda:certification>
            </cbvmda:certificationList>
        </ilmd>
    </extension>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Bing Fishing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</cbvmda:informationProvider>
</ObjectEvent>
```

**Fishing Event #2**
```xml
<!-- FISHING EVENT -->
<ObjectEvent>
    <eventTime>2020-01-27T2:00:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>2743D44E-4E20-4237-BA68-1842F3173790</eventID>
    </baseExtension>
    <epcList/>
    <action>ADD</action>
    <bizStep>urn:epcglobal:cbv:bizstep:commissioning</bizStep>
    <disposition>urn:epcglobal:cbv:disp:active</disposition>
    <readPoint>
        <id>geo:38.258151,-123.875288</id>
    </readPoint>

    <!-- BING Ship -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.47797660-9355-4f8c-8867-c98ee1e8b684</id>
    </bizLocation>

    <extension>
        <quantityList>

            <!-- YELLOW FIN TUNA -->
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT.LOT2222</epcClass>
                <quantity>2500.0</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <ilmd>

            <!-- CATCH INFORMATION -->
            <cbvmda:vesselCatchInformationList>
                <cbvmda:vesselCatchInformation>

                    <!-- FAO ZONE 77 -->
                    <cbvmda:catchArea>77</cbvmda:catchArea>

                    <!-- GEAR TYPE: Beam Trawls -->
                    <cbvmda:fishingGearTypeCode>TBB</cbvmda:fishingGearTypeCode>
                </cbvmda:vesselCatchInformation>
            </cbvmda:vesselCatchInformationList>

            <!-- WILD HARVEST -->
            <productionMethodForFishAndSeafoodCode>MARINE_FISHERY</productionMethodForFishAndSeafoodCode>
            
            <cbvmda:harvestStartDate>2020-01-27</cbvmda:harvestStartDate>
            <cbvmda:harvestEndDate>2020-01-27</cbvmda:harvestEndDate>

            <!-- CATCH CERTIFICATE (?) -->
            <cbvmda:certificationList>
                <cbvmda:certification>
                    <gdst:certificateType>urn:gdst:certType:catch_certificate</gdst:certificateType>
                    <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
                    <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
                    <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
                    <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
                </cbvmda:certification>
            </cbvmda:certificationList>
        </ilmd>
    </extension>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Bing Fishing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</cbvmda:informationProvider>
</ObjectEvent>
```

**Fishing Event #3**
```xml
<!-- FISHING EVENT -->
<ObjectEvent>
    <eventTime>2020-01-27T2:00:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>2743D44E-4E20-4237-BA68-1842F3173790</eventID>
    </baseExtension>
    <epcList/>
    <action>ADD</action>
    <bizStep>urn:epcglobal:cbv:bizstep:commissioning</bizStep>
    <disposition>urn:epcglobal:cbv:disp:active</disposition>
    <readPoint>
        <id>geo:38.184786,-123.776411</id>
    </readPoint>

    <!-- BING Ship -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.47797660-9355-4f8c-8867-c98ee1e8b684</id>
    </bizLocation>

    <extension>
        <quantityList>

            <!-- YELLOW FIN TUNA -->
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT.LOT3333</epcClass>
                <quantity>2500.0</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <ilmd>

            <!-- CATCH INFORMATION -->
            <cbvmda:vesselCatchInformationList>
                <cbvmda:vesselCatchInformation>

                    <!-- FAO ZONE 77 -->
                    <cbvmda:catchArea>77</cbvmda:catchArea>

                    <!-- GEAR TYPE: Beam Trawls -->
                    <cbvmda:fishingGearTypeCode>TBB</cbvmda:fishingGearTypeCode>
                </cbvmda:vesselCatchInformation>
            </cbvmda:vesselCatchInformationList>

            <!-- WILD HARVEST -->
            <productionMethodForFishAndSeafoodCode>MARINE_FISHERY</productionMethodForFishAndSeafoodCode>
            
            <cbvmda:harvestStartDate>2020-01-27</cbvmda:harvestStartDate>
            <cbvmda:harvestEndDate>2020-01-27</cbvmda:harvestEndDate>

            <!-- CATCH CERTIFICATE (?) -->
            <cbvmda:certificationList>
                <cbvmda:certification>
                    <gdst:certificateType>urn:gdst:certType:catch_certificate</gdst:certificateType>
                    <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
                    <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
                    <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
                    <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
                </cbvmda:certification>
            </cbvmda:certificationList>
        </ilmd>
    </extension>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Bing Fishing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</cbvmda:informationProvider>
</ObjectEvent>
```

**Fishing Event #4**
```xml
<!-- FISHING EVENT -->
<ObjectEvent>
    <eventTime>2020-01-27T2:00:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>2743D44E-4E20-4237-BA68-1842F3173790</eventID>
    </baseExtension>
    <epcList/>
    <action>ADD</action>
    <bizStep>urn:epcglobal:cbv:bizstep:commissioning</bizStep>
    <disposition>urn:epcglobal:cbv:disp:active</disposition>
    <readPoint>
        <id>geo:38.115669,-123.655561</id>
    </readPoint>

    <!-- BING Ship -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.47797660-9355-4f8c-8867-c98ee1e8b684</id>
    </bizLocation>

    <extension>
        <quantityList>

            <!-- YELLOW FIN TUNA -->
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT.LOT4444</epcClass>
                <quantity>2500.0</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <ilmd>

            <!-- CATCH INFORMATION -->
            <cbvmda:vesselCatchInformationList>
                <cbvmda:vesselCatchInformation>

                    <!-- FAO ZONE 77 -->
                    <cbvmda:catchArea>77</cbvmda:catchArea>

                    <!-- GEAR TYPE: Beam Trawls -->
                    <cbvmda:fishingGearTypeCode>TBB</cbvmda:fishingGearTypeCode>
                </cbvmda:vesselCatchInformation>
            </cbvmda:vesselCatchInformationList>

            <!-- WILD HARVEST -->
            <productionMethodForFishAndSeafoodCode>MARINE_FISHERY</productionMethodForFishAndSeafoodCode>
            
            <cbvmda:harvestStartDate>2020-01-27</cbvmda:harvestStartDate>
            <cbvmda:harvestEndDate>2020-01-27</cbvmda:harvestEndDate>

            <!-- CATCH CERTIFICATE -->
            <cbvmda:certificationList>
                <cbvmda:certification>
                    <gdst:certificateType>urn:gdst:certType:catch_certificate</gdst:certificateType>
                    <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
                    <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
                    <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
                    <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
                </cbvmda:certification>
            </cbvmda:certificationList>
        </ilmd>
    </extension>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Bing Fishing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</cbvmda:informationProvider>
</ObjectEvent>
```