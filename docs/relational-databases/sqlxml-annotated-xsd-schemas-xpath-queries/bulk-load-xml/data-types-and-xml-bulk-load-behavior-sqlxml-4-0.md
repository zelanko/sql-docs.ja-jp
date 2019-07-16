---
title: データ型と XML 一括読み込みの動作 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 820d2b083544542d1c1414f978105fe992b0ce36
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915147"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>データ型と XML 一括読み込みの動作 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  マッピング スキーマで指定されているデータ型 (XSD または XDR 型と**sql:datatype**)、通常は無視されます、次の場合を除きます。  
  
 XSD では、次の場合に注意してください。  
  
-   型の場合**dateTime**または**時間**を指定する必要があります、 **sql:datatype** XML 一括読み込みは、Microsoftにデータを送信する前にデータ変換を実行するため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   列に一括読み込みを行うときに**uniqueidentifier**入力[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、XSD 値は中かっこ ({、}) を含む GUID を指定する必要があります**sql:datatype ="uniqueidentifier"** に値が列に挿入される前に、中かっこを削除します。 場合**sql:datatype**が指定されていない、かっこで、値が送信され、挿入は失敗します。  
  
 詳細については**sql:datatype**を参照してください[データ型の強制型変換と sql:datatype 注釈&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)します。  
  
 XDR では、次の場合に注意してください。  
  
-   場合、 **dt:type**は**datetime**、**時間**、 **dateTime.tz**、または**time.tz**、両方を指定する必要があります**dt:type**と**sql:datatype**データ型にデータを送信する前に、XML 一括読み込みはデータ変換を実行するため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
-   型の場合は、XML データ**uuid**、 **sql:datatype**指定する必要があります。**dt:type ="uuid"** しない限り、データは、文字列データが必要でも。 指定しない場合**dt:uuid**、XML 一括読み込みを中かっこの文字列を受け取る (および必要な場合に、それらを削除します)。  
  
-   XML データがある場合**bin.base64**または**マップされる bin.hex**で XML データ型を指定する必要があります**dt:type**します。 指定すると、XML 一括読み込みではデータを 16 進数表記として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込みます。  
  
  
