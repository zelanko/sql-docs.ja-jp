---
title: SQL Server のメッセージ結果 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7dc6cfb5388634e9e2f4281250dd7eb619102515
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106751"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを生成しない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの行セットまたはカウントの影響を受ける行の実行時。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 実行に成功、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは S_OK を返すし、メッセージが使用できる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、S_OK を返しますあり、1 つまたは複数情報メッセージの多くの実行に使用可能な[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはのコンシューマーの実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマー クエリ テキストの動的な指定を許可するがすべてメンバー関数の実行後に、値に関係なく、リターン コードが存在するか、返されたのエラーインターフェイスを確認する必要があります**IRowset**または**IMultipleResults**インターフェイスの参照、または影響を受ける行の数。  
  
## <a name="see-also"></a>関連項目  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
