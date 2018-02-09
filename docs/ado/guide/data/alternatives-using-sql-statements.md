---
title: "他の方法: SQL ステートメントの使用 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
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
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 85831e635103ec622414af7a77d545fb470c3f7e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
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
