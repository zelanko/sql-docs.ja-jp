---
title: SQL Server のメッセージ結果 |Microsoft ドキュメント
description: SQL Server のメッセージ結果
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 71036d3e97fcaf13f11f4e9fda741b9983902039
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントは SQL Server の行セットまたは実行時に影響を受けた行のカウントの OLE DB ドライバーを生成しません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 正常に実行される、S_OK を返すと、OLE DB Driver for SQL Server と、メッセージは、OLE DB Driver for SQL Server コンシューマーを使用できます。  
  
 SQL Server の OLE DB Driver は、S_OK を返しますおり、1 つまたは複数の情報メッセージの多くの実行を次に利用可能な[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントや、OLE DB Driver for SQL Server メンバー関数のコンシューマー実行します。  
  
 クエリ テキストの動的な指定を許可する SQL Server コンシューマーの OLE DB Driver は各メンバー関数の実行後に、値に関係なく、リターン コードの有無、返されるエラー インターフェイスを確認する必要があります**IRowset**または**IMultipleResults**インターフェイスの参照、または影響を受けた行の数。  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
