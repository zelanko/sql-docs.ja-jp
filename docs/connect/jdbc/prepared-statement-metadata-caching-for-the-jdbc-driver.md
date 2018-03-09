---
title: "JDBC Driver のキャッシュ ステートメント メタデータの準備 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13d4c0766552d9472038ffe7f2ff7fed6d73584d
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>JDBC Driver のキャッシュの準備されたステートメント メタデータ
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この記事では、ドライバーのパフォーマンスを強化するために実装されている 2 つの変更について説明します。

## <a name="batching-of-unprepare-for-prepared-statements"></a>準備されたステートメント用 Unprepare のバッチ処理
バージョン 6.1.6-preview、パフォーマンスが向上が最小限に抑えることで実装されていたためサーバーのラウンド トリップを SQL Server。 以前は、各 prepareStatement クエリの unprepare への呼び出しも送信されました。 ドライバーがここで、バッチ処理が最大しきい値"ServerPreparedStatementDiscardThreshold"は、10 の既定値を持つクエリの準備を解除します。

> [!NOTE]  
>  ユーザーは次のメソッドを使用して既定値を変更することができます: setServerPreparedStatementDiscardThreshold (int 値)

6.1.6-preview から導入された 1 つ以上の変更は、前に、このドライバーは常に呼び出すこと sp_prepexec です。 ここで、準備されたステートメントの最初の実行、ドライバーは、sp_executesql を呼び出すし、残りの部分に sp_prepexec を実行しハンドルを割り当てます。 詳細を参照して[ここ](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching)です。

> [!NOTE]  
>  ユーザーは、既定の動作を変更する設定 enablePrepareOnFirstPreparedStatementCall sp_prepexec 常に呼び出すことは、以前のバージョンに**true**次のメソッドを使用します。setEnablePrepareOnFirstPreparedStatementCall (ブール値)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>この変更によりのバッチ処理の導入された新しい Api の一覧の準備されたステートメントの準備を解除

 **SQLServerConnection**
 
|新しいメソッド|Description|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|準備済み現在未解決の数を返しますステートメント操作の準備を解除します。|
|void closeUnreferencedPreparedStatementHandles()|実行する、未処理破棄された準備されたステートメント用 unprepare 要求を強制します。|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|特定の接続のインスタンスの動作を返します。 False の場合は最初の実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 つ目の実行の動作と、ステートメントを準備できず、実際に準備されたステートメント ハンドルをセットアップします。 次の実行呼び出し sp_execute します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。 このオプションの既定値は、呼び出し元 setDefaultEnablePrepareOnFirstPreparedStatementCall() で変更できます。|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|特定の接続のインスタンスの動作を指定します。 値が false の場合、最初に実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 つ目の実行の動作と、ステートメントを準備できず、実際に準備されたステートメント ハンドルをセットアップします。 次の実行呼び出し sp_execute します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|int getServerPreparedStatementDiscardThreshold()|特定の接続のインスタンスの動作を返します。 この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 場合は、設定は、< = 1, unprepare アクションは、準備されたステートメント閉じるですぐに実行されます。 設定されている場合は、{@literal >} 1、これらの呼び出しは、まとめてバッチ処理が多すぎるため呼び出し sp_unprepare のオーバーヘッドを回避します。 このオプションの既定値は、呼び出し元 getDefaultServerPreparedStatementDiscardThreshold() で変更できます。|
|void setServerPreparedStatementDiscardThreshold(int value)|特定の接続のインスタンスの動作を指定します。 この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 場合は、設定は、< = 1 のアクションを準備解除準備されたステートメントを閉じるには直ちに実行されます。 > 1 に設定されている場合は、これらの呼び出しはまとめてバッチ処理 sp_unprepare の多くの呼び出しのオーバーヘッドを回避します。|

 **SQLServerDataSource**
 
|新しいメソッド|Description|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|この構成が false の場合、準備されたステートメントの最初の実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 つ目の実行の動作と、ステートメントを準備できず、実際に準備されたステートメント ハンドルをセットアップします。 次の実行呼び出し sp_execute します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|この構成は、準備されたステートメントの最初の実行が sp_executesql を呼び出す場合は false を返し、2 つ目の実行後、ステートメントを準備できません、sp_prepexec を呼び出すし、実際に準備されたステートメント ハンドルをセットアップします。 次の実行呼び出し sp_execute します。 これから解放 sp_unprepare 準備されたステートメントでの必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 場合は、設定は、< = 1 のアクションを準備解除準備されたステートメントを閉じるには直ちに実行されます。 設定されている場合は、{@literal >} 1 これらの呼び出しが頻繁すぎる sp_unprepare の呼び出しのオーバーヘッドを避けるためにまとめてバッチ処理|
|int getServerPreparedStatementDiscardThreshold()|この設定は、どのくらい未処理準備操作 (sp_unprepare) 保留にできる 1 つの接続、サーバー上の保留状態のハンドルをクリーンアップする呼び出しが実行される前にステートメントの破棄を制御します。 場合は、設定は、< = 1 のアクションを準備解除準備されたステートメントを閉じるには直ちに実行されます。 設定されている場合は、{@literal >} 1 これらの呼び出しが頻繁すぎる sp_unprepare の呼び出しのオーバーヘッドを避けるためにまとめてバッチ処理します。|

## <a name="prepared-statement-metatada-caching"></a>準備済みステートメント メタデータのキャッシュ
6.3.0-preview バージョンの時点では、Microsoft SQL Server 用 JDBC driver は、準備されたステートメント キャッシュをサポートします。 V6.3.0-プレビューする前に既に準備ができているおよび、キャッシュに格納されているクエリが実行されるいずれかの場合、同じクエリを再度呼び出すことは発生しません準備します。 ここで、ドライバーはキャッシュにクエリを検索ハンドルを取得して sp_execute を実行します。
準備済みステートメント メタデータ キャッシュが**無効になっている**既定です。 これを有効にするためには、接続オブジェクトで、次のメソッドを呼び出す必要があります。

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

例えば： `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>この変更により、準備されたステートメントの導入された新しい Api の一覧のメタデータのキャッシュ

 **SQLServerConnection**
 
|新しいメソッド|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|ステートメントのプールを true または false に設定します。|
|boolean getDisableStatementPooling()|ステートメントのプールが無効になっている場合は true を返します。|
|void setStatementPoolingCacheSize(int value)|この接続の準備されたステートメント キャッシュのサイズを指定します。 1 より小さい値には、キャッシュ、なしです。|
|int getStatementPoolingCacheSize()|この接続の準備されたステートメント キャッシュのサイズを返します。 1 より小さい値には、キャッシュ、なしです。|
|int getStatementHandleCacheEntryCount()|プールされた準備されたステートメント ハンドルの現在の数を返します。|
|boolean isPreparedStatementCachingEnabled()|ステートメントのプールが有効になっているかどうか、またはこの接続ではありません。|

 **SQLServerDataSource**
 
|新しいメソッド|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|ステートメント プーリングを true または false に設定します。|
|boolean getDisableStatementPooling()|ステートメントのプールが無効になっている場合は true を返します。|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|この接続の準備されたステートメント キャッシュのサイズを指定します。 1 より小さい値には、キャッシュ、なしです。|
|int getStatementPoolingCacheSize()|この接続の準備されたステートメント キャッシュのサイズを返します。 1 より小さい値には、キャッシュ、なしです。|

## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性の強化](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
