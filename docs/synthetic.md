

```xml
<?xml version="1.0"?>
<!--

    Copyright 2014-2019 XebiaLabs Inc. and its affiliates. Use is subject to terms of the enclosed Legal Notice.

-->
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
        xmlns="http://www.xebialabs.com/deployit/synthetic"
        targetNamespace="http://www.xebialabs.com/deployit/synthetic"
        elementFormDefault="qualified">

    <xs:element name="synthetic">
        <xs:complexType>
            <xs:choice maxOccurs="unbounded" minOccurs="0">
                <xs:element name="type" type="SyntheticTypeDefinition"/>
                <xs:element name="type-modification" type="SyntheticTypeModification"/>
            </xs:choice>
        </xs:complexType>
    </xs:element>

    <xs:complexType name="SyntheticTypeDefinition">
        <xs:sequence>
            <xs:element name="generate-deployable" type="SyntheticDeployableGeneration" minOccurs="0" maxOccurs="1"/>
            <xs:element name="icon" type="xs:string" minOccurs="0" maxOccurs="1"/>
            <xs:element name="property" type="SyntheticPropertyDefinition" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="method" type="SyntheticMethodDefinition" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="rule" type="SyntheticValidationRule" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="verification" type="SyntheticVerification" minOccurs="0" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="type" type="DeployitTypeName" use="required"/>

        <xs:attribute name="extends" type="DeployitTypeName" use="required"/>
        <xs:attribute name="label" type="xs:string" />
        <xs:attribute name="root" type="xs:string" />
        <xs:attribute name="rootName" type="xs:string" />
        <xs:attribute name="description" type="xs:string"/>
        <xs:attribute name="virtual" type="xs:boolean"/>
        <xs:attribute name="versioned" type="xs:boolean"/>
        <xs:attribute name="inspectable" type="xs:boolean"/>
        <xs:attribute name="deployable-type" type="DeployitTypeName"/>
        <xs:attribute name="container-type" type="DeployitTypeName"/>
    </xs:complexType>

    <xs:complexType name="SyntheticDeployableGeneration">
        <xs:attribute name="type" type="DeployitTypeName" use="required"/>
        <xs:attribute name="extends" type="DeployitTypeName" use="required"/>
        <xs:attribute name="description" type="xs:string"/>
        <xs:attribute name="copy-default-values" type="xs:boolean"/>
        <xs:attribute name="virtual" type="xs:boolean"/>
    </xs:complexType>

    <xs:complexType name="SyntheticTypeModification">
        <xs:sequence minOccurs="1" maxOccurs="unbounded">
            <xs:element name="property" type="SyntheticPropertyDefinition" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="method" type="SyntheticMethodDefinition" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="rule" type="SyntheticValidationRule" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="verification" type="SyntheticVerification" minOccurs="0" maxOccurs="unbounded"/>
        </xs:sequence>
        <xs:attribute name="type" type="DeployitTypeName" use="required"/>
        <xs:attribute name="versioned" type="xs:boolean"/>
    </xs:complexType>

    <xs:complexType name="SyntheticPropertyDefinition">
        <xs:sequence>
            <xs:element name="rule" type="SyntheticValidationRule" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="enum-values" minOccurs="0" maxOccurs="1">
                <xs:complexType>
                    <xs:sequence minOccurs="1">
                        <xs:element name="value" minOccurs="1" maxOccurs="unbounded" />
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
            <xs:element name="input-hint" type="SyntheticInputHint" minOccurs="0" maxOccurs="1" />
        </xs:sequence>
        <xs:attribute name="name" type="JavaPropertyName" use="required"/>
        <xs:attribute name="kind" type="KindType"/>
        <xs:attribute name="description" type="xs:string"/>
        <xs:attribute name="category" type="xs:string"/>
        <xs:attribute name="label" type="xs:string"/>
        <xs:attribute name="required" type="xs:boolean"/>
        <xs:attribute name="password" type="xs:boolean"/>
        <xs:attribute name="size" type="SizeType"/>
        <xs:attribute name="default" type="xs:string"/>
        <xs:attribute name="enum-class" type="xs:string"/>
        <xs:attribute name="referenced-type" type="DeployitTypeName"/>
        <xs:attribute name="as-containment" type="xs:boolean"/>
        <xs:attribute name="hidden" type="xs:boolean"/>
        <xs:attribute name="transient" type="xs:boolean"/>
        <xs:attribute name="readonly" type="xs:boolean"/>
        <xs:attribute name="inspectionProperty" type="xs:boolean"/>
        <xs:attribute name="aliases" type="xs:string"/>
        <xs:attribute name="candidate-values-filter" type="xs:string" />
    </xs:complexType>

    <xs:complexType name="SyntheticMethodDefinition">
        <xs:sequence minOccurs="0" maxOccurs="1">
            <xs:element name="parameters">
                <xs:complexType>
                    <xs:sequence minOccurs="1" maxOccurs="unbounded">
                        <xs:element name="parameter" type="SyntheticPropertyDefinition"/>
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
        </xs:sequence>
        <xs:attribute name="name" type="JavaPropertyName" use="required"/>
        <xs:attribute name="label" type="xs:string"/>
        <xs:attribute name="description" type="xs:string"/>
        <xs:attribute name="delegate" type="xs:string" use="optional"/>
        <xs:attribute name="parameters-type" type="DeployitTypeName" use="optional"/>
        <xs:anyAttribute processContents="skip"/>
    </xs:complexType>

    <xs:complexType name="SyntheticValidationRule">
        <xs:attribute name="type" type="xs:string" default="regex"/>
        <xs:anyAttribute processContents="skip"/>
    </xs:complexType>

    <xs:complexType name="SyntheticVerification">
        <xs:attribute name="type" type="xs:string" default=""/>
    </xs:complexType>

    <xs:complexType name="SyntheticInputHint">
        <xs:sequence>
            <xs:element name="rule" type="SyntheticValidationRule" minOccurs="0" maxOccurs="unbounded"/>
            <xs:element name="values" minOccurs="0" maxOccurs="1">
                <xs:complexType>
                    <xs:sequence minOccurs="1">
                        <xs:element name="value" minOccurs="1" maxOccurs="unbounded" type="SyntheticValue" />
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
            <xs:element name="prompt" minOccurs="0" maxOccurs="1" type="xs:string" />
            <xs:element name="copy-from-property" minOccurs="0" maxOccurs="1" type="xs:string" />
        </xs:sequence>
    </xs:complexType>

    <xs:complexType name="SyntheticValue">
        <xs:simpleContent>
            <xs:extension base="xs:string">
                <xs:attribute name="label" type="xs:string"/>
            </xs:extension>
        </xs:simpleContent>
    </xs:complexType>

    <xs:simpleType name="JavaPropertyName">
        <xs:restriction base="xs:string">
            <xs:pattern value="[a-zA-Z0-9_]*"/>
        </xs:restriction>
    </xs:simpleType>

    <xs:simpleType name="JavaClassName">
        <xs:restriction base="xs:string">
            <xs:pattern value="([a-zA-Z_$][a-zA-Z\d_$]*\.)*[a-zA-Z_$][a-zA-Z\d_$]*"/>
        </xs:restriction>
    </xs:simpleType>

    <xs:simpleType name="DeployitTypeName">
        <xs:restriction base="xs:string">
            <xs:pattern value="[a-zA-Z0-9.-]+\.[a-zA-Z0-9-]+"/>
        </xs:restriction>
    </xs:simpleType>

    <xs:simpleType name="KindType">
        <xs:restriction base="xs:string">
            <xs:enumeration value="enum"/>
            <xs:enumeration value="boolean"/>
            <xs:enumeration value="integer"/>
            <xs:enumeration value="string"/>
            <xs:enumeration value="date"/>
            <xs:enumeration value="ci"/>
            <xs:enumeration value="set_of_ci"/>
            <xs:enumeration value="set_of_string"/>
            <xs:enumeration value="map_string_string"/>
            <xs:enumeration value="list_of_ci"/>
            <xs:enumeration value="list_of_string"/>
        </xs:restriction>
    </xs:simpleType>

    <xs:simpleType name="SizeType">
        <xs:restriction base="xs:string">
            <xs:enumeration value="default"/>
            <xs:enumeration value="small"/>
            <xs:enumeration value="medium"/>
            <xs:enumeration value="large"/>
        </xs:restriction>
    </xs:simpleType>

</xs:schema>
```