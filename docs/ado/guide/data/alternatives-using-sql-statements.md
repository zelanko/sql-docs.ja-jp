---
title: '代替手段: SQL ステートメントの使用 |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f41ef7f0641877056a6e2f3d85fd6a40ff7826db
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925997"
---
# <a name="alternatives-using-sql-statements"></a>代替: SQL ステートメントの使用
ADO では、データを編集するための組み込みプロパティやメソッドの代わりにコマンドを使用することもできます。 プロバイダーによっては、このセクションに記載されているすべての操作を、データソースにコマンドを渡すことによって実現することもできます。 たとえば、SQL UPDATE ステートメントを使用して、**フィールド**の**Value**プロパティを使用せずにデータを変更できます。 SQL INSERT ステートメントは、ADO メソッド**AddNew**ではなく、データソースに新しいレコードを追加するために使用できます。 プロバイダーの SQL またはデータ操作言語の詳細については、データソースのドキュメントを参照してください。  
  
 たとえば、次のコードに示すように、DELETE ステートメントを含む SQL 文字列をデータベースに渡すことができます。  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
