---
title: SQLSRV Driver API Reference | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a05b7a39bce6fb263b63bdbfa4644c78175a584c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928238"
---
# <a name="sqlsrv-driver-api-reference"></a>SQLSRV ドライバー API リファレンス
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] の SQLSRV ドライバーの API 名は **sqlsrv**です。 すべての **sqlsrv** 関数は、先頭に **sqlsrv_** が付き、動詞または名詞が続きます。 動詞が続く関数は何らかのアクションを実行し、名詞が続く関数は、何らかの形式のメタデータを返します。  
  
## <a name="in-this-section"></a>このセクションの内容  
SQLSRV ドライバーには、次の関数が含まれています。  
  
|Function|説明|  
|------------|---------------|  
|[sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)|トランザクションを開始します。|  
|[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)|ステートメントを取り消します。ステートメントの保留中の結果がある場合は破棄します。|  
|[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)|クライアントに関する情報を提供します。|  
|[sqlsrv_close](../../connect/php/sqlsrv-close.md)|接続を閉じます。 接続に関連付けられているすべてのリソースを解放します。|  
|[sqlsrv_commit](../../connect/php/sqlsrv-commit.md)|トランザクションをコミットします。|  
|[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)|エラー処理とログの構成を変更します。|  
|[sqlsrv_connect](../../connect/php/sqlsrv-connect.md)|接続を作成して開きます。|  
|[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)|最後の操作に関するエラーおよび警告の情報を返します。|  
|[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)|準備されたステートメントを実行します。|  
|[sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)|次のデータ行を読み取り可能にします。|  
|[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)|次のデータ行を数値インデックス配列、連想配列、またはその両方として取得します。|  
|[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)|オブジェクトとしてデータの次の行を取得します。|  
|[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)|フィールドのメタデータを返します。|  
|[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)|ステートメントを閉じます。 ステートメントに関連付けられているすべてのリソースを解放します。|  
|[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)|指定された構成設定の値を返します。|  
|[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)|インデックスを指定して現在の行のフィールドを取得します。 PHP の戻り値の型を指定できます。|  
|[sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md)|結果セットの行数が 1 以上の場合に検出します。|  
|[sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md)|次の結果を処理可能にします。|  
|[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)|結果セットの行数をレポートします。|  
|[sqlsrv_num_fields](../../connect/php/sqlsrv-num-fields.md)|アクティブな結果セット内のフィールド数を取得します。|  
|[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)|Transact-SQL クエリを実行せずに準備します。 パラメーターを暗黙的にバインドします。|  
|[sqlsrv_query](../../connect/php/sqlsrv-query.md)|Transact-SQL クエリを準備して実行します。|  
|[sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)|トランザクションをロールバックします。|  
|[sqlsrv_rows_affected](../../connect/php/sqlsrv-rows-affected.md)|変更された行数を返します。|  
|[sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)|関数の呼び出しごとに、最大 8 KB のデータをサーバーに送信します。|  
|[sqlsrv_server_info](../../connect/php/sqlsrv-server-info.md)|サーバーに関する情報を提供します。|  
  
## <a name="reference"></a>リファレンス  
[PHP マニュアル](https://php.net/manual)  
  
## <a name="see-also"></a>参照  
[Microsoft SQL Server 用 Drivers for PHP の概要](../../connect/php/overview-of-the-php-sql-driver.md)

[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[SQL Server 用 Microsoft Drivers for PHP のためのプログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)

[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/getting-started-with-the-php-sql-driver.md)
  
