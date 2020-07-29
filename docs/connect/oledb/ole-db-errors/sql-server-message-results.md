---
title: SQL Server のメッセージ結果 | Microsoft Docs
description: SQL Server のメッセージ結果
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: dfebd7443b24d09e6bf7696caba5449c1890e0d2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "85998282"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、OLE DB Driver for SQL Server の行セットや、ステートメント実行時に処理された行カウントは生成されません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 実行に成功すると、OLE DB Driver for SQL Server から S_OK が返され、OLE DB Driver for SQL Server コンシューマーはメッセージを利用できるようになります。  
  
 多くの [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントの実行後、またはコンシューマーでの OLE DB Driver for SQL Server のメンバー関数の実行後、OLE DB Driver for SQL Server は S_OK を返し、1 つまたは複数の情報メッセージが利用できるようになります。  
  
 OLE DB Driver for SQL Server のコンシューマーがクエリ テキストの動的な指定を許可する場合、メンバー関数を実行するたびにエラー インターフェイスをチェックする必要があります。このチェックは、リターン コードの値、返される **IRowset** インターフェイス参照や **IMultipleResults** インターフェイス参照の有無、および処理された行数に関係なく行う必要があります。  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
