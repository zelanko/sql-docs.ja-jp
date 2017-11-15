---
title: "timestamp データ型に対する FOR XML サポート | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: timestamp data type
ms.assetid: 4e1920e1-e7a4-4069-965e-3f6039a6099e
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5c40d3f480861e98ef0cdf3f40a6ff22a739de6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="for-xml-support-for-the-timestamp-data-type"></a>timestamp データ型に対する FOR XML サポート
  FOR XML 変換では、 **timestamp** 型の値は、 **varbinary(8)** データとして扱われ、常に、Base 64 エンコードされます。 必要に応じて、XSD スキーマまたは XDR スキーマでこの型が反映されます。  
  
```  
drop table t  
go  
create table t  
(c1 int,  
 c2 timestamp)  
go  
  
insert t values(1, null)  
go  
select * from t  
for xml auto, xmldata  
go  
```  
  
 結果を次に示します。  
  
```  
<Schema name="Schema1"   
        xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="t" content="empty" model="closed">  
    <AttributeType name="c1" dt:type="i4" />  
    <AttributeType name="c2" dt:type="bin.base64" />  
    <attribute type="c1" />  
    <attribute type="c2" />  
  </ElementType>  
</Schema>  
<t xmlns="x-schema:#Schema1" c1="1" c2="AAAAAAAAH04=" />  
```  
  
## <a name="see-also"></a>参照  
 [各種 SQL Server データ型の FOR XML サポート](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
