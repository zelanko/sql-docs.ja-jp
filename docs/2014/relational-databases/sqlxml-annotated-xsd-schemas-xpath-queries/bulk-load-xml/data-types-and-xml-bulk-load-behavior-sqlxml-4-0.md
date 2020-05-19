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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e36b895bdb7c0ade6674525ad94677b1444082a5
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703417"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>データ型と XML 一括読み込みの動作 (SQLXML 4.0)
  マッピング スキーマで指定されるデータ型 (XSD または XDR 型と `sql:datatype`) は、次の場合を除いて、通常は無視されます。  
  
 XSD では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、型が `dateTime` または `time` の場合は、`sql:datatype` を指定する必要があります。  
  
-   の型の列に一括読み込みを実行するときに、 `uniqueidentifier` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XSD 値が中かっこ ({および}) を含む GUID である場合、 **sql: datatype = "uniqueidentifier"** を指定して、列に値を挿入する前に中かっこを削除する必要があります。 `sql:datatype` を指定しない場合、値はかっこ付きで送られ、挿入は失敗します。  
  
 の詳細については `sql:datatype` 、「[データ型の強制型変換」および「sql: datatype 注釈 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)」を参照してください。  
  
 XDR では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、`dt:type` が `datetime`、`time`、`dateTime.tz`、または `time.tz` の場合は、`dt:type` と `sql:datatype` データ型の両方を指定する必要があります。  
  
-   XML データの型がである場合は `uuid` 、を `sql:datatype` 指定する必要があります。データが文字列データの場合を除き、 **dt: type = "uuid"** も必要です。 `dt:uuid` を指定しない場合、XML 一括読み込みでは中かっこ付きの文字列が読み込まれ、必要に応じて削除されます。  
  
-   XML データが `bin.base64` または `bin.hex` の場合は、`dt:type` で XML データ型を指定する必要があります。 指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。  
  
  
