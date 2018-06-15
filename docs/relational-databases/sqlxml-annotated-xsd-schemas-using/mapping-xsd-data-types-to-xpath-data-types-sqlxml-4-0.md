---
title: XPath データ型 (SQLXML 4.0) に XSD データ型のマッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
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
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b41676bcf1cfe655fd7ed7f5c68b5b924c0f9814
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32969707"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>XSD データ型から XPath データ型へのマッピング (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XSD スキーマに対して XPath クエリが実行され、XSD 型がで指定された、 **xsd:type**属性、XPath を使用してクエリを処理するときに指定されたデータ型。  
  
 ノードの XPath データ型は、次の表に示すように、スキーマ内に指定されている XSD データ型から派生します。 ここでは説明のため、EmployeeID というノードを使用します。  
  
|XSD データ型|XDR データ型|同等の<br /><br /> XPath データ型|SQL Server<br /><br /> SQL Server 変換|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**なし**<br /><br /> **bin.base64bin.hex**|**適用なし**|なし<br /><br /> EmployeeID|  
|**ブール値**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**10 進数、整数、浮動小数点数、バイト、short、int、long、float、double、unsignedByte、unsignedShort、unsignedInt、unsignedLong**|**数、int、float、i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8**|**number**|CONVERT(float(53), EmployeeID)|  
|**id、idref、idrefsentity、entities、表記法、nmtoken、nmtokens、DateTime、string、AnyURI**|**id、idref、idrefsentity、entities、列挙、表記、nmtoken、nmtokens、char、dateTime、dateTime.tz、文字列、uri、uuid**|**文字列**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**該当なし (はデータ型は、XDR データ型 fixed14.4 に相当する XPath のです。)**|CONVERT(money, EmployeeID)|  
|**date**|**date**|**文字列**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**time**|**time**<br /><br /> **time.tz**|**文字列**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
