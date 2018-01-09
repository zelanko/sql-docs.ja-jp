---
title: "SQL Server のメッセージ結果 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-errors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be4cde80aa97b0216c9879c892fc1bc4a54cfe1a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを生成しない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]影響を受ける行の実行時の Native Client OLE DB プロバイダーの行セットまたはのカウント。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 正常に実行される、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは S_OK を返すし、メッセージは使用できます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは S_OK が返され、1 つまたは複数の情報メッセージの多くの実行を次に利用可能なは[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはのコンシューマーの実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ テキストの動的な指定を許可する Native Client OLE DB プロバイダーのコンシューマーはすべてメンバー関数の実行後に、値に関係なく、リターン コードの有無、返されるエラー インターフェイスを確認する必要があります**IRowset**または**IMultipleResults**インターフェイスの参照、または影響を受けた行の数。  
  
## <a name="see-also"></a>参照  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
