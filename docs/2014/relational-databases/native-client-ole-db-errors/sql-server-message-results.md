---
title: SQL Server のメッセージ結果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
ms.openlocfilehash: aa63445b81ec89b87523fa29c50817e128d48515
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043556"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
  次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの行セット、または実行時に影響を受ける行の数を生成しません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 正常に実行される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、Native client OLE DB プロバイダーは S_OK を返します。メッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーコンシューマーが使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB プロバイダーは S_OK を返し、多くのステートメントの実行後、 [!INCLUDE[tsql](../../includes/tsql-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーメンバー関数のコンシューマー実行に従って、1つまたは複数の情報メッセージを使用できるようにします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーコンシューマーは、クエリテキストを動的に指定できるようにするため、リターンコードの値、返される**IRowset**または**IMultipleResults**インターフェイス参照の有無、または影響を受ける行の数に関係なく、すべてのメンバー関数の実行後にエラーインターフェイスをチェックする必要があります。  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
