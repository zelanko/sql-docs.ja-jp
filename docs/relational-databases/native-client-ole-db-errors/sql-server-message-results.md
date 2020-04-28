---
title: SQL Server のメッセージ結果 | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 577b609fd2f878e6c97010cac004e0b10b3a4e4e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300977"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  次[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントは、Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーの行セット、または実行時に影響を受ける行の数を生成しません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 正常に実行される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、native client OLE DB プロバイダーは S_OK を返します。メッセージは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、native client OLE DB プロバイダーコンシューマーが使用できます。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client OLE DB プロバイダーは S_OK を返し、多く[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントの実行後、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーメンバー関数のコンシューマー実行に従って、1つまたは複数の情報メッセージを使用できるようにします。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーコンシューマーは、クエリテキストを動的に指定できるようにするため、リターンコードの値、返される**IRowset**または**IMultipleResults**インターフェイス参照の有無、または影響を受ける行の数に関係なく、すべてのメンバー関数の実行後にエラーインターフェイスをチェックする必要があります。  
  
## <a name="see-also"></a>参照  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
