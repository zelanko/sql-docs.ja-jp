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
ms.openlocfilehash: 44ec3198bfb6f9898406688df2544dd2e243294b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39459486"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC Driver の JDBC 4.3 への準拠

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Microsoft JDBC Driver 6.4 for SQL Server より前のバージョンは、Java Database Connectivity (JDBC) API 4.2 仕様にのみ準拠しています。 このセクションは、6.4 リリースより前のバージョンには適用されません。

Microsoft JDBC Driver for SQL Server バージョン 6.4 では、JAVA 9 の互換性をスローします`SQLFeatureNotSupportedException`の新しい JDBC 4.3 Api メソッドが実装されていません。

SQL Server リリースの Microsoft JDBC Driver 7.0、ドライバーが現在 JAVA 10 の互換性のあるにあり、以下をサポートする Api の説明になります。 ドライバーをスロー `SQLFeatureNotSupportedException` JDBC 4.3 仕様から実装されていない他のメソッド。

|新しい API|[説明]|注目に値する実装|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|この接続での作業の独立した単位の要求を開始しているドライバーへのヒント。 詳細については、「[java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--)」を参照してください。|API のパブリック メソッドを変更することは接続のフィールドの値を保存します: `databaseAutoCommitMode`、 `transactionIsolationLevel`、 `networkTimeout`、 `holdability`、 `sendTimeAsDatetime`、 `statementPoolingCacheSize`、 `disableStatementPooling`、 `serverPreparedStatementDiscardThreshold`、 `enablePrepareOnFirstPreparedStatementCall `、`catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void java.sql.connection.endRequest()|要求、独立した単位の作業が完了したドライバーへのヒント。 詳細については、「[java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--)」を参照してください。|作業単位間に作成されたステートメントを終了し、開いているトランザクションをロールバックします。 メソッドには、上記の接続フィールドへの変更も元に戻します。|
