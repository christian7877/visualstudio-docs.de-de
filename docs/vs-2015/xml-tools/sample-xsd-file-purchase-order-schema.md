---
title: 'XSD-Beispieldatei: Bestellungsschema | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 36f9817f2007efbf92b03c7d718e6004d91931ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521802"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>XSD-Beispieldatei: Bestellungsschema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [XSD-Beispieldatei: Bestellungsschema](https://docs.microsoft.com/visualstudio/xml-tools/sample-xsd-file-purchase-order-schema).  
  
  
Die folgende XSD-Datei wird in verschiedenen Beispielen in der Dokumentation zum XSD-Schema-Designer verwendet. Bei dieser Datei handelt es sich um ein Bestellungsschema.  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
          elementFormDefault="qualified">  
  <xsd:element name='comment' type='xsd:string'/>  
  
  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>  
  
  <xsd:complexType name='USAddress'>  
    <xsd:annotation>  
      <xsd:documentation>  
        Purchase order schema for Example.Microsoft.com.  
      </xsd:documentation>  
    </xsd:annotation>  
    <xsd:sequence>  
      <xsd:element name='name'   type='xsd:string'/>  
      <xsd:element name='street' type='xsd:string'/>  
      <xsd:element name='city'   type='xsd:string'/>  
      <xsd:element name='state'  type='xsd:string'/>  
      <xsd:element name='zip'    type='xsd:decimal'/>  
    </xsd:sequence>  
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>  
  </xsd:complexType>  
  
  <xsd:simpleType name='SKU'>  
    <xsd:restriction base='xsd:string'>  
      <xsd:pattern value='\d{3}\w{3}'/>  
    </xsd:restriction>  
  </xsd:simpleType>  
  
  <xsd:complexType name='Items'>  
    <xsd:sequence>  
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name='productName' type='xsd:string'/>  
            <xsd:element name='quantity'>  
              <xsd:simpleType>  
                <xsd:restriction base='xsd:positiveInteger'>  
                  <xsd:minInclusive value='1'/>  
                  <xsd:maxExclusive value='100'/>  
                </xsd:restriction>  
              </xsd:simpleType>  
            </xsd:element>  
            <xsd:element name='USPrice'  type='xsd:decimal'/>  
            <xsd:element ref='tns:comment'/>  
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>  
          </xsd:sequence>  
          <xsd:attribute name='partNum' type='tns:SKU'/>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  
  <xsd:complexType name='PurchaseOrderType'>  
    <xsd:sequence>  
      <xsd:element name='shipTo' type='tns:USAddress'/>  
      <xsd:element name='billTo' type='tns:USAddress'/>  
      <xsd:element ref='tns:comment' minOccurs='0'/>  
      <xsd:element name='items'  type='tns:Items'/>  
    </xsd:sequence>  
    <xsd:attribute name='orderDate' type='xsd:date'/>  
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>  
  </xsd:complexType>  
</xsd:schema>  
```


