---
title: "catalog.cleanup_server_execution_keys |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79f1006-54e8-4cbf-96f8-5ed143ebb830
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 172925d5a63aa831881b6a6325f0dbcbccd4dd56
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcleanupserverexecutionkeys"></a>catalog.cleanup_server_execution_keys
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SSISDB データベースから証明書と対称キーを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
            cleanup_server_execution_keys [ @cleanup_flag = ] cleanup_flag ,  
[ @delete_batch_size = ] delete_batch_size  
  
```  
  
## <a name="arguments"></a>引数  
 [ @cleanup_flag =] *cleanup_flag*  
 実行レベル (1) またはプロジェクト レベル (2) 証明書と対称キーがドロップされるかどうかを示します。  
  
 PER_EXECUTION (1) を SERVER_OPERATION_ENCRYPTION_LEVEL が設定されている場合にのみ、実行レベル (1) を使用します。  
  
 SERVER_OPERATION_ENCRYPTION_LEVEL が PER_PROJECT (2) に設定されている場合にのみ、プロジェクト レベル (2) を使用します。 証明書と対称キーは、削除された、および操作ログが消去されてプロジェクトに対してのみ削除されます。  
  
 [ @delete_batch_size =] *delete_batch_size*  
 キーおよび削除する証明書の数。 既定値は 1000 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功と失敗の 1 は 0 です。  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   読み取り権限と実行、プロジェクトと、該当する場合、参照先の環境に対する読み取りアクセス許可。  
  
-   メンバーシップ、 **ssis_admin**データベース ロール。  
  
-   メンバーシップを**sysadmin**サーバーの役割です。  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 このストアド プロシージャでは、次のシナリオでエラーが発生します。  
  
-   SSISDB データベースに 1 つまたは複数のアクティブな操作があります。  
  
-   SSISDB データベースがシングル ユーザー モードではないです。  
  
## <a name="remarks"></a>解説  
 SQL Server 2012 Service Pack 2 を SERVER_OPERATION_ENCRYPTION_LEVEL プロパティの追加、 **internal.catalog_properties**テーブル。 このプロパティでは、2 つの値には。  
  
-   **PER_EXECUTION (1)** – 証明書と対称キーが機密性の高い実行パラメーターを保護するために使用して、実行ログは、実行のたびに作成されます。 これが既定値です。 実行ごとに証明書/キーが生成されるため、運用環境でパフォーマンスの問題 (デッドロック、失敗したメンテナンス ジョブなど) に発生する可能性があります。 ただし、この設定は、その他の値 (2) よりも高いレベルのセキュリティを提供します。  
  
-   **PER_PROJECT (2)** – 証明書と機微なパラメーターを保護するために使用する対称キーは、プロジェクトごとに作成されます。 これにより、PER_EXECUTION レベルより優れたパフォーマンス、キーと証明書が生成 1 回実行するたびにではなく、プロジェクトのため。  
  
 実行する必要がある、 [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md)ストアド プロシージャを SERVER_OPERATION_ENCRYPTION_LEVEL を変更するには、1 ~ 2 (または) 1 を 2 からにします。 ストアド プロシージャを実行して、前に、次の作業を行います。  
  
1.  OPERATION_CLEANUP_ENABLED プロパティの値が TRUE に設定されていることを確認してください、 [catalog.catalog_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)テーブル。  
  
2.  Integration Services データベース (SSISDB) をシングル ユーザー モードに設定します。 SQL Server Management Studio で SSISDB 用のデータベースのプロパティ ダイアログ ボックスを起動、オプション タブに切り替えますおよびアクセスの制限プロパティをシングル ユーザー モード (SINGLE_USER) に設定します。 Cleanup_server_log を実行した後は、ストアド プロシージャでは、元の値にプロパティ値を設定します。  
  
3.  ストアド プロシージャを実行[catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md)です。  
  
4.  ここで、さあ、SERVER_OPERATION_ENCRYPTION_LEVEL プロパティの値を変更、 [catalog.catalog_properties & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)テーブル。  
  
5.  ストアド プロシージャを実行[catalog.cleanup_server_execution_keys](../../integration-services/system-stored-procedures/catalog-cleanup-server-execution-keys.md) SSISDB データベースから証明書のキーをクリーンアップします。 SSISDB データベースから証明書とキーを削除するため、オフピーク時間中に定期的に実行する必要があります、長い時間がかかる場合があります。  
  
     スコープまたはレベル (プロジェクトとの比較の実行) および削除するキーの数を指定することができます。 削除の既定のバッチ サイズは 1000 です。 2、レベルを設定するときに、関連するプロジェクトが削除されている場合にのみ、キーと証明書が削除されました。  
  
 詳細については、次のサポート技術情報の記事を参照してください。 [SQL Server 2012 で修正: パフォーマンスの問題として、展開 SSISDB を使用すると保存します。](http://support.microsoft.com/kb/2972285)  
  
## <a name="example"></a>例  
 次の例では、cleanup_server_execution_keys ストアド プロシージャを呼び出します。  
  
```tsql  
USE [SSISDB]  
GO  
  
DECLARE@return_value int  
  
EXEC@return_value = [internal].[cleanup_server_execution_keys]  
@cleanup_flag = 1,  
@delete_batch_size = 500  
  
SELECT'Return Value' = @return_value  
  
GO  
  
```  
  
  
