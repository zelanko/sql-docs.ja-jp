---
title: データ型と XML 一括読み込みの動作 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d2eb9af2b353760f5b195b95d6a9f9d5d1efc9b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013417"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>データ型と XML 一括読み込みの動作 (SQLXML 4.0)
  マッピング スキーマで指定されるデータ型 (XSD または XDR 型と `sql:datatype`) は、次の場合を除いて、通常は無視されます。  
  
 XSD では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから Microsoft `dateTime` にデータが送信されるため、型が `time` または `sql:datatype` の場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定する必要があります。  
  
-   の`uniqueidentifier` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]型の列に一括読み込みを実行するときに、XSD 値が中かっこ ({および}) を含む GUID である場合、 **sql: datatype = "uniqueidentifier"** を指定して、列に値を挿入する前に中かっこを削除する必要があります。 
  `sql:datatype` を指定しない場合、値はかっこ付きで送られ、挿入は失敗します。  
  
 の詳細につい`sql:datatype`ては、「[データ型の強制型変換」および「Sql: DATATYPE 注釈 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)」を参照してください。  
  
 XDR では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから `dt:type` にデータが送信されるため、`datetime` が `time`、`dateTime.tz`、`time.tz`、または `dt:type` の場合は、`sql:datatype` と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型の両方を指定する必要があります。  
  
-   XML データの型`uuid`がである場合`sql:datatype`は、を指定する必要があります。データが文字列データの場合を除き、 **dt: type = "uuid"** も必要です。 
  `dt:uuid` を指定しない場合、XML 一括読み込みでは中かっこ付きの文字列が読み込まれ、必要に応じて削除されます。  
  
-   XML データが `bin.base64` または `bin.hex` の場合は、`dt:type` で XML データ型を指定する必要があります。 指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。  
  
  
