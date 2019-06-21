---
title: JDBC Driver の準備されたステートメント メタデータ キャッシュ | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 58ebcb2560e3b03703d7a419b28c6c04e41c19f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794087"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>JDBC Driver の準備されたステートメント メタデータ キャッシュ
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この記事では、ドライバーのパフォーマンスを強化するために実装されている 2 つの変更について説明します。

## <a name="batching-of-unprepare-for-prepared-statements"></a>準備されたステートメント用 Unprepare のバッチ処理
サーバーのラウンド トリップを SQL Server をバージョン 6.1.6-preview、パフォーマンスの向上が最小限に抑えることで実装されるためです。 以前は、各 prepareStatement クエリの unprepare への呼び出しも送信されました。 ドライバーが次に、バッチ処理が最大しきい値"ServerPreparedStatementDiscardThreshold"は、10 の既定値を持つクエリを準備解除します。

> [!NOTE]  
>  ユーザーは次のメソッドを使用して既定値を変更することができます: setServerPreparedStatementDiscardThreshold (int 値)

6\.1.6-preview から導入されたもう 1 つの変更は、その前に、ドライバーが常に呼び出される sp_prepexec です。 ここで、最初に、準備されたステートメントの実行、ドライバーは、sp_executesql を呼び出すし、rest、sp_prepexec を実行し、識別するハンドルを割り当てます。 詳細を参照して[ここ](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching)します。

> [!NOTE]  
>  ユーザーは、以前のバージョンを設定する enablePrepareOnFirstPreparedStatementCall、sp_prepexec を常に呼び出しを既定の動作を変更することができます**true**次のメソッドを使用して。setEnablePrepareOnFirstPreparedStatementCall (ブール値)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>準備されたステートメント用のバッチ処理のため、この変更で導入された新しい Api の一覧が Unprepare

 **SQLServerConnection**
 
|新しいメソッド|[説明]|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|準備された現在未解決の数を返すステートメント unprepare アクション。|
|void closeUnreferencedPreparedStatementHandles()|強制的に実行される、卓越した破棄された準備されたステートメント用 unprepare 要求をします。|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|特定の接続のインスタンスの動作を返します。 False の場合、最初の実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 番目の実行が発生すると、ステートメントは準備および準備されたステートメント ハンドルを実際にセットアップします。 次の実行呼び出し sp_execute します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。 このオプションの既定値は、呼び出し元 setDefaultEnablePrepareOnFirstPreparedStatementCall() で変更できます。|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|特定の接続のインスタンスの動作を指定します。 値が false の場合、最初の実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 番目の実行が発生すると、ステートメントは準備および準備されたステートメント ハンドルを実際にセットアップします。 次の実行呼び出し sp_execute します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|int getServerPreparedStatementDiscardThreshold()|特定の接続のインスタンスの動作を返します。 この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 設定の場合 < = 1、unprepare 準備のステートメントを閉じる操作が直ちに実行されます。 設定されている場合は、{@literal >} 1、これらの呼び出しはまとめて頻度が高すぎる sp_unprepare 呼び出しのオーバーヘッドを回避するためにします。 このオプションの既定値は、呼び出し元 getDefaultServerPreparedStatementDiscardThreshold() で変更できます。|
|void setServerPreparedStatementDiscardThreshold(int value)|特定の接続のインスタンスの動作を指定します。 この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 設定の場合 < = 1 unprepare アクション準備されたステートメントを閉じるには直ちに実行されます。 > 1 に設定されている場合の頻度が高すぎる sp_unprepare の呼び出しのオーバーヘッドを回避するためにこれらの呼び出しはまとめてバッチします。|

 **SQLServerDataSource**
 
|新しいメソッド|[説明]|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|この構成が false の場合、準備されたステートメントの最初の実行が sp_executesql を呼び出すと sp_prepexec を呼び出す 2 番目の実行が発生すると、ステートメントは準備および準備されたステートメント ハンドルを実際にセットアップします。 次の実行呼び出し sp_execute します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|この構成が、準備されたステートメントの最初の実行は、sp_executesql を呼び出す場合は false を返し、2 番目の実行が発生すると、ステートメントを準備できない場合は、sp_prepexec を呼び出すし、実際に準備されたステートメント ハンドルをセットアップします。 次の実行呼び出し sp_execute します。 これによって準備されたステートメントで sp_unprepare の必要性閉じる場合は、ステートメントは 1 回だけ実行します。|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 設定の場合 < = 1 unprepare アクション準備されたステートメントを閉じるには直ちに実行されます。 設定されている場合は、{@literal >} 1 sp_unprepare の頻度が高すぎる呼び出しのオーバーヘッドを回避するためにこれらの呼び出しがまとめてバッチ処理|
|int getServerPreparedStatementDiscardThreshold()|この設定は、数未処理準備操作 (sp_unprepare) は、サーバー上で未処理のハンドルをクリーンアップする呼び出しが実行される前に 1 接続あたりの未処理できますステートメントの破棄を制御します。 設定の場合 < = 1 unprepare アクション準備されたステートメントを閉じるには直ちに実行されます。 設定されている場合は、{@literal >} 1 sp_unprepare の頻度が高すぎる呼び出しのオーバーヘッドを回避するためにこれらの呼び出しがまとめてバッチ処理します。|

## <a name="prepared-statement-metatada-caching"></a>準備されたステートメント メタデータ キャッシュ
6\.3.0-preview のバージョンの時点では、Microsoft SQL Server 用 JDBC driver は、準備されたステートメント キャッシュをサポートします。 V6.3.0-preview では、前に既に準備され、キャッシュに格納されているクエリを実行する 1 つの場合、同じクエリをもう一度呼び出すことは発生しませんに準備します。 ここで、ドライバー キャッシュでクエリを検索ハンドルと sp_execute でそれを実行します。
準備されたステートメント メタデータ キャッシュが**無効になっている**既定。 これを有効にするためには、接続オブジェクトで、次のメソッドを呼び出す必要があります。

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

例: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>準備されたステートメントのこの変更で導入された新しい Api の一覧のメタデータのキャッシュ

 **SQLServerConnection**
 
|新しいメソッド|[説明]|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|ステートメントのプールを true または false に設定します。|
|boolean getDisableStatementPooling()|ステートメントのプールが無効になっている場合は true を返します。|
|void setStatementPoolingCacheSize(int value)|この接続の準備されたステートメント キャッシュのサイズを指定します。 1 より小さい値には、キャッシュがありません。|
|int getStatementPoolingCacheSize()|この接続の準備されたステートメント キャッシュのサイズを返します。 1 より小さい値には、キャッシュがありません。|
|int getStatementHandleCacheEntryCount()|プールされた準備されたステートメント ハンドルの現在の数を返します。|
|boolean isPreparedStatementCachingEnabled()|ステートメントのプールが有効になっているかどうか、またはこの接続ではありません。|

 **SQLServerDataSource**
 
|新しいメソッド|[説明]|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|ステートメント プーリングを true または false に設定します。|
|boolean getDisableStatementPooling()|ステートメントのプールが無効になっている場合は true を返します。|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|この接続の準備されたステートメント キャッシュのサイズを指定します。 1 より小さい値には、キャッシュがありません。|
|int getStatementPoolingCacheSize()|この接続の準備されたステートメント キャッシュのサイズを返します。 1 より小さい値には、キャッシュがありません。|

## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性の強化](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
