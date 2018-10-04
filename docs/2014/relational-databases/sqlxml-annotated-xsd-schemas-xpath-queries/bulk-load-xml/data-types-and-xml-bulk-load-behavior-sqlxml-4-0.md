---
title: データ型と XML 一括読み込みの動作 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95471d8e7db5fdde76a561e09b6d5ad96057165f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117332"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>データ型と XML 一括読み込みの動作 (SQLXML 4.0)
  マッピング スキーマで指定されるデータ型 (XSD または XDR 型と `sql:datatype`) は、次の場合を除いて、通常は無視されます。  
  
 XSD では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、型が `dateTime` または `time` の場合は、`sql:datatype` を指定する必要があります。  
  
-   列に一括読み込みを行うときに`uniqueidentifier`入力[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、XSD 値は中かっこ ({、}) を含む GUID を指定する必要があります**sql:datatype ="uniqueidentifier"** 値は、前に、中かっこを削除するには列に挿入します。 `sql:datatype` を指定しない場合、値はかっこ付きで送られ、挿入は失敗します。  
  
 詳細については`sql:datatype`を参照してください[データ型の強制型変換と sql:datatype 注釈&#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)します。  
  
 XDR では、次の場合に注意してください。  
  
-   XML 一括読み込みではデータ変換が実行されてから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にデータが送信されるため、`dt:type` が `datetime`、`time`、`dateTime.tz`、または `time.tz` の場合は、`dt:type` と `sql:datatype` データ型の両方を指定する必要があります。  
  
-   型の場合は、XML データ`uuid`、`sql:datatype`指定する必要があります。**dt:type ="uuid"** しない限り、データは、文字列データが必要でも。 `dt:uuid` を指定しない場合、XML 一括読み込みでは中かっこ付きの文字列が読み込まれ、必要に応じて削除されます。  
  
-   XML データが `bin.base64` または `bin.hex` の場合は、`dt:type` で XML データ型を指定する必要があります。 指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。  
  
  
