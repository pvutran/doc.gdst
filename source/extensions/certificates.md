---
title: Certificates
description: This covers how Certificates have been extended including Certificate Types and where Certificates can be added.
---

Certificates were extended in 2 ways. The first way is that Certificate Type was added as a KDE to each certificate to indicate the role in Seafood Traceability that certificate was playing. The next is that the base Object event was extended to allow for a list of Certificates outside of the ILMD data. So that Products could have Certificate information after they have been created.

## Certificate Type

The Certificate Type is specified using the following attribute underneath the `gdst` namespace.
`<gdst:certificationType></gdst:certificationType>`

An example of this in use is as following:
```xml
<cbvmda:certificationList>
        <cbvmda:certification>
            <gdst:certificationType>urn:gdst:certType:harvestCert</gdst:certificationType>
            <cbvmda:certificationStandard>NM6</cbvmda:certificationStandard>
            <cbvmda:certificationAgency>DFO</cbvmda:certificationAgency>
            <cbvmda:certificationValue>SIMP.LPCO.2</cbvmda:certificationValue>
            <cbvmda:certificationIdentification>10161781</cbvmda:certificationIdentification>
      </cbvmda:certification>
</cbvmda:certificationList>
```

## List of Certificate Types
| Certificate Type | Description |
| ----------- | ----------- |
| `urn:gdst:certType:fishingAuth` | Unique number associated with a regulatory document, from the relevant authority, granting permission for wild-capture of seafood by a fisher or fishing vessel. |
| `urn:gdst:certType:harvestCert` | Name of harvest standards body which a particular harvest seafood is subject to and the unique identifier associated with the certified entity. |
| `urn:gdst:certType:harvestCoC` | Name of chain of custody standards body which particular harvest seafood is subject to and the unique identifier associated with the certified entity. |
| `urn:gdst:certType:transshipmentAuth` | Unique number associated with a regulatory document, from the relevant authority, granting permission for discharge of wild-capture of seafood from a fishing vessel to a transshipment vessel. |
| `urn:gdst:certType:landingAuth` | Unique number associated with a regulatory document, from the relevant authority, granting permission for discharge of wild-capture of seafood to land by a fisher, fishing vessel or transshipment vessel. |
| `urn:gdst:certType:humanPolicy` | Name of internationally recognized standards to which policy on a vessel/trip claims conformity. |
| `urn:gdst:certType:processorLicense` | Unique indicator generated by the authorities in the country of operation that gives the processor the license to operate. |
| `urn:gdst:certType:aggregatorLicense` | Unique indicator generated by the authorities in the country of operation that gives the aggregator the license to operate. |

## Object Event Certifications

The base Object event in EPCIS was extended with `<gdst:certificationList></gdst:certificationList>` to allow for certificate to be specified on events that ILMD data is not allowed.

```xml
<!-- TRANSSHIPMENT EVENT -->
<ObjectEvent>
    <eventTime>2019-01-28T18:12:00Z</eventTime>
    <eventTimeZoneOffset>+00:00</eventTimeZoneOffset>
    <baseExtension>
        <eventID>EEC77B23-E1BF-484D-BE2C-7CBC4EBB4F9A</eventID>
    </baseExtension>
    <epcList/>
    <action>OBSERVE</action>
    <bizStep>urn:gdst:bizStep:transshipment</bizStep>
    <disposition>urn:gdst:entering_commerce</disposition>
    

    <!-- Jimmy's Tender Vessel -->
    <bizLocation>
        <id>urn:gdst:traceability-solution.com:location:loc:0048000.019283"</id>
    </bizLocation>

    <!-- Transshipment Location -->
    <readPoint>
        <id>geo:37.860236,-123.144697</id>
    </readPoint>

    <extension>

        <!-- YELLOW FIN TUNA -->
        <quantityList>
            <quantityElement>
                <epcClass>urn:gdst:traceability-solution.com:product:lot:class:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7.YFT-FILLET.LOT20203015</epcClass>
                <quantity>5000</quantity>
                <uom>KGM</uom>
            </quantityElement>
        </quantityList>

        <!-- SELLER: Bing Fishing Co.-->
        <sourceList>
            <source type="urn:epcglobal:cbv:sdt:owning_party">urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</source>
        </sourceList>

        <!-- BUYER: Jimmy's Processing Co. -->
        <destinationList>
            <destination type="urn:epcglobal:cbv:sdt:owning_party">urn:gdst:traceability-solution.com:party:0048000.000001</destination>
        </destinationList>
    </extension>

    <!-- Certification List Extension -->
    <gdst:certificationList>

        <!-- Transshipment Authorization -->
        <cbvmda:certification>
            <gdst:certificateType>urn:gdst:certType:transshipment_authorization</gdst:certificateType>
            <cbvmda:certificationStandard>Transshipment Authority</cbvmda:certificationStandard>
            <cbvmda:certificationAgency>Transshipment Authority</cbvmda:certificationAgency>
            <cbvmda:certificationValue>TA_123456789</cbvmda:certificationValue>
            <cbvmda:certificationIdentification>TA_123456789</cbvmda:certificationIdentification>
        </cbvmda:certification>

        <!-- Chain of Custody -->
        <cbvmda:certification>
            <gdst:certificateType>urn:gdst:certType:chain_custody</gdst:certificateType>
            <cbvmda:certificationStandard>MSC Chain of Custody</cbvmda:certificationStandard>
            <cbvmda:certificationAgency>MSC</cbvmda:certificationAgency>
            <cbvmda:certificationValue>MSC_COC_1234567890</cbvmda:certificationValue>
            <cbvmda:certificationIdentification>MSC_COC_1234567890</cbvmda:certificationIdentification>
        </cbvmda:certification>

    </gdst:certificationList>

    <!-- Bing Fishing Co. -->
    <gdst:productOwner>urn:gdst:traceability-solution.com:party:0b4e59bb-29ba-4edd-8e51-7e8d1a96dce7</gdst:productOwner>

    <!-- Jimmy's Processing Co. -->
    <cbvmda:informationProvider>urn:gdst:traceability-solution.com:party:0048000.000001</cbvmda:informationProvider>
</ObjectEvent>
```