---
title: "他の方法: SQL ステートメントの使用 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 325c9a9a75083a17ffda0f19c8521c3f36f8104e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="alternatives-using-sql-statements"></a>他の方法: SQL ステートメントの使用
ADO では、その組み込みプロパティおよびデータを編集するためのメソッドの代わりに、コマンドを使用することもできます。 プロバイダーによっては、すべての操作がこのセクションで説明することもできます、データ ソースにコマンドを渡すことによってです。 SQL UPDATE ステートメントを使用してを使用せずにデータを変更するなど、**値**のプロパティ、**フィールド**です。 SQL の INSERT ステートメントは、ADO メソッドではなく、データ ソースに新しいレコードを追加するために使用できます**AddNew**です。 SQL またはプロバイダーのデータ操作言語の詳細については、データ ソースのマニュアルを参照してください。  
  
 たとえば、次のコードに示すように、データベースへの DELETE ステートメントを含む SQL 文字列を渡すことができます。  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
