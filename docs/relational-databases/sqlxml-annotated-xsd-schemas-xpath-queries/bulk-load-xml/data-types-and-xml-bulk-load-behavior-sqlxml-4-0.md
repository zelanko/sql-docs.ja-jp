---
title: "データ型と XML 一括読み込み動作 (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d5e25e9d3a2df2e15c2dc9bf86d6d90acd1d450
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>データ型と XML 一括読み込みの動作 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
マッピング スキーマで指定されているデータ型 (XSD または XDR 型と**sql:datatype**) は、通常は無視されますでは、次の場合。  
  
 XSD では、次の場合に注意してください。  
  
-   型の場合**dateTime**または**時間**を指定する必要があります、 **sql:datatype** XML 一括読み込みは、Microsoftにデータを送信する前にデータ変換を実行するため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   列に一括読み込みを行うときに**uniqueidentifier**に入力[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、XSD 値は中かっこ ({、}) を含む GUID を指定する必要があります**sql:datatype = uniqueidentifier**に列に値を挿入する前に、中かっこを削除します。 場合**sql:datatype**が指定されていない、値が中かっこで送信され、挿入は失敗します。  
  
 詳細については**sql:datatype**を参照してください[データ型の強制変換と sql:datatype 注釈 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XDR では、次の場合に注意してください。  
  
-   場合、 **dt:type**は**datetime**、**時間**、 **dateTime.tz**、または**time.tz**、両方を指定する必要があります**dt:type**と**sql:datatype**データ型にデータを送信する前に、XML 一括読み込みがデータ変換を実行するため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。  
  
-   型の場合は、XML データ**uuid**、 **sql:datatype**指定する必要があります。**dt:type ="uuid"**も必要です、データが文字列データです。 指定しない場合**dt:uuid**、XML 一括読み込みは中かっこで文字列を受け入れ (および必要に応じて削除されます)。  
  
-   XML データは、場合**bin.base64**または**bin.hex**、XML データ型を指定する必要があります**dt:type**です。 指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。  
  
  
