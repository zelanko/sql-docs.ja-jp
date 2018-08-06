---
title: JDBC 4.3 JDBC Driver のコンプライアンス |Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f529c88044444f3fb6e428b6c69f5a5cf5917251
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278913"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC Driver の JDBC 4.3 への準拠
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Microsoft JDBC Driver 6.4 for SQL Server より前のバージョンのドライバーは、Java Database Connectivity (JDBC) API 4.2 仕様に準拠しています。 このセクションは、6.4 リリースより前のバージョンには適用されません。  
  
 バージョン 6.4 では、SQL Server 用 Microsoft JDBC Driver は JAVA 10 の互換性があるが、JDBC API 4.3 仕様に完全に準拠はありません。 ドライバーは、未実装のメソッドの SQLFeatureNotSupportedException をスローします。 
 
 次の JDBC 4.3 API のメソッドは、SQL Server 用 Microsoft JDBC Driver 6.4 で実装されます。
 
  **SQLServerConnection クラス**  
  
|新しいメソッド|[説明]|注目に値する実装|  
|-----------------|-----------------|-------------------------------|  
|beginRequest() を無効にします。|この接続での作業の独立した単位の要求を開始しているドライバーへのヒント。 詳細については、「[java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--)」を参照してください。|API のパブリック メソッドを変更することは接続のフィールドの値を保存します: `databaseAutoCommitMode`、 `transactionIsolationLevel`、 `networkTimeout`、 `holdability`、 `sendTimeAsDatetime`、 `statementPoolingCacheSize`、 `disableStatementPooling`、 `serverPreparedStatementDiscardThreshold`、 `enablePrepareOnFirstPreparedStatementCall `、`catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void endRequest()|要求、独立した単位の作業が完了したドライバーへのヒント。 詳細については、「[java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--)」を参照してください。|作業単位間に作成されたステートメントを終了し、開いているトランザクションをロールバックします。 メソッドには、上記の接続フィールドへの変更も元に戻します。|