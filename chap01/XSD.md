## admi.002.spi.1.3.xsd

```xml
<?xml version='1.0' encoding="UTF-8"?>
<xs:schema xmlns:xs='http://www.w3.org/2001/XMLSchema'
           targetNamespace='https://www.bcb.gov.br/pi/admi.002/1.3'
           xmlns='https://www.bcb.gov.br/pi/admi.002/1.3'
           elementFormDefault='qualified'>

    <xs:element name="Envelope" type="SPIEnvelopeMessage"/>

    <xs:complexType name="SPIEnvelopeMessage">
        <xs:sequence>
            <xs:element name="AppHdr" type="SPI.head.001.001.01"/>
            <xs:element name="Document" type="SPI.admi.002.001.01"/>
        </xs:sequence>
    </xs:complexType>

    <!-- inicio BAH -->
    <xs:complexType name="SPI.head.001.001.01">
        <xs:sequence>
            <xs:element name="Fr" type="Party9Choice"/>
            <xs:element name="To" type="Party9Choice"/>
            <xs:element name="BizMsgIdr" type="MsgIdType"/>
            <xs:element name="MsgDefIdr" type="Max35Text"/>
            <xs:element name="CreDt" type="ISONormalisedDateTime"/>
            <xs:element name="Sgntr" type="SignatureEnvelope"/>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="BranchAndFinancialInstitutionIdentification5">
        <xs:sequence>
            <xs:element name="FinInstnId" type="FinancialInstitutionIdentification8"/>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="FinancialInstitutionIdentification8">
        <xs:sequence>
            <xs:element name="Othr" type="GenericFinancialIdentification1"/>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="GenericFinancialIdentification1">
        <xs:sequence>
            <xs:element name="Id" type="ISPBType"/>
        </xs:sequence>
    </xs:complexType>
    <xs:simpleType name="ISONormalisedDateTime">
        <xs:restriction base="xs:dateTime">
            <xs:pattern value="[0-9]{4}-[0-9]{2}-[0-9]{2}T[0-9]{2}:[0-9]{2}:[0-9]{2}\.[0-9]{3}Z"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="ISPBType">
        <xs:restriction base="xs:string">
            <xs:maxLength value="8"/>
            <xs:pattern value="[0-9]{8}"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="Max35Text">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"/>
            <xs:maxLength value="35"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="MsgIdType">
        <xs:restriction base="xs:string">
            <xs:maxLength value="32"/>
            <xs:pattern value="[M][0-9]{8}[a-zA-Z0-9]{23}"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:complexType name="Party9Choice">
        <xs:choice>
            <xs:element name="FIId" type="BranchAndFinancialInstitutionIdentification5"/>
        </xs:choice>
    </xs:complexType>
    <xs:complexType name="SignatureEnvelope">
        <xs:sequence>
            <xs:any namespace="http://www.w3.org/2000/09/xmldsig#"/>
        </xs:sequence>
    </xs:complexType>
    <!-- fim BAH -->

    <!-- inicio ISO -->
    <xs:complexType name="SPI.admi.002.001.01">
        <xs:sequence>
            <xs:element name="admi.002.001.01" type="admi.002.001.01"/>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="admi.002.001.01">
        <xs:sequence>
            <xs:element name="RltdRef" type="MessageReference"/>
            <xs:element name="Rsn" type="RejectionReason2"/>
        </xs:sequence>
    </xs:complexType>
    <xs:simpleType name="Max1000Text">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"/>
            <xs:maxLength value="1000"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="Max33Text">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"/>
            <xs:maxLength value="33"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="Max350Text">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"/>
            <xs:maxLength value="350"/>
        </xs:restriction>
    </xs:simpleType>
    <xs:complexType name="MessageReference">
        <xs:sequence>
            <xs:element name="Ref" type="Max33Text"/>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="RejectionReason2">
        <xs:sequence>
            <xs:element name="RjctgPtyRsn" type="Max35Text"/>
            <xs:element minOccurs="0" name="RjctnDtTm" type="ISONormalisedDateTime"/>
            <xs:element minOccurs="0" name="ErrLctn" type="Max350Text"/>
            <xs:element minOccurs="0" name="RsnDesc" type="Max350Text"/>
            <xs:element minOccurs="0" name="AddtlData" type="Max1000Text"/>
        </xs:sequence>
    </xs:complexType>
    <!-- fim ISO -->

</xs:schema>
```

