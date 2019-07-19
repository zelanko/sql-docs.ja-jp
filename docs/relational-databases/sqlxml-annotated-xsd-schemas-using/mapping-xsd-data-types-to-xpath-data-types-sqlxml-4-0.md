---
title: XPath データ型 (SQLXML 4.0) への XSD データ型のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a7f79a4d756a76dc6b59e76bbbfc28076ba36eae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067049"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>XSD データ型から XPath データ型へのマッピング (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XSD スキーマに対して XPath クエリが実行され、XSD 型がで指定された、 **xsd:type**属性、XPath を使用して、クエリの処理時に指定されたデータ型。  
  
 ノードの XPath データ型は、次の表に示すように、スキーマ内に指定されている XSD データ型から派生します。 ここでは説明のため、EmployeeID というノードを使用します。  
  
|XSD データ型|XDR データ型|同等の表記<br /><br /> XPath データ型|SQL Server<br /><br /> SQL Server 変換|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**None**<br /><br /> **bin.base64bin.hex**|**適用なし**|なし<br /><br /> EmployeeID|  
|**ブール値**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**10 進数、整数、浮動小数点数、バイト、short、int、long、float、double、unsignedByte、unsignedShort、unsignedInt、unsignedLong**|**数、int、float、i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8**|**number**|CONVERT(float(53), EmployeeID)|  
|**id、idref、idrefsentity、エンティティ、表記、nmtoken、nmtokens、DateTime、string、AnyURI**|**id、idref、idrefsentity、エンティティ、列挙、表記、nmtoken、nmtokens、char、dateTime、dateTime.tz、文字列、uri、uuid**|**string**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**該当なし (はデータ型は XDR データ型 fixed14.4 に相当する XPath の。)**|CONVERT(money, EmployeeID)|  
|**date**|**date**|**string**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**time**|**time**<br /><br /> **time.tz**|**string**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
