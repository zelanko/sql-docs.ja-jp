---
title: "sp_syscollector_create_collection_set (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_set_TSQL
- sp_syscollector_create_collection_set
dev_langs: TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_create_collection_set
ms.assetid: 69e9ff0f-c409-43fc-89f6-40c3974e972c
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23015f77f4d2bc9dafe10fb12b660cec31484985
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spsyscollectorcreatecollectionset-transact-sql"></a>sp_syscollector_create_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいコレクション セットを作成します。 このストアド プロシージャを使用すると、データ コレクション用のカスタム コレクション セットを作成できます。  
  
> [!WARNING]  
>  プロキシとして構成されている Windows アカウントがまだログインしていない非対話型または対話型のユーザーの場合、プロファイル ディレクトリは存在せず、ステージング ディレクトリの作成は失敗します。 したがって、ドメイン コントローラーでプロキシ アカウントを使用している場合は、プロファイル ディレクトリが確実に作成されているようにするため、少なくとも 1 回は使用されている対話型アカウントを指定する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_create_collection_set   
      [ @name = ] 'name'  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    , [ [ @schedule_uid = ] 'schedule_uid' ]  
    , [ [ @schedule_name = ] 'schedule_name' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
    , [ @collection_set_id = ] collection_set_id OUTPUT   
    , [ [ @collection_set_uid = ] 'collection_set_uid' OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@name =** ] '*名前*'  
 コレクション セットの名前を指定します。 *名前*は**sysname**空の文字列または NULL にすることはできません。  
  
 *名前*一意である必要があります。 現在のコレクション セットの名前の一覧については、syscollector_collection_sets システム ビューにクエリを実行します。  
  
 [  **@target =** ] '*ターゲット*'  
 将来の使用のために予約されています。 *名前*は**nvarchar (128)**で、既定値は NULL です。  
  
 [  **@collection_mode =** ] *collection_mode*  
 データを収集し、格納する方法を指定します。 *collection_mode*は**smallint**値は次のいずれかを持つことができます。  
  
 0 - キャッシュ モード。 データの収集とアップロードは個別のスケジュールに従います。 連続コレクションのキャッシュ モードを指定します。  
  
 1 - 非キャッシュ モード。 データの収集とアップロードは、同じスケジュールでです。 アドホック コレクションまたはスナップショット コレクションの非キャッシュ モードを指定します。  
  
 既定値*collection_mode*は 0 です。 ときに*collection_mode* 0 の場合は、 *schedule_uid*または*schedule_name*指定する必要があります。  
  
 [  **@days_until_expiration =** ] *days_until_expiration*  
 収集したデータを管理データ ウェアハウスに保管しておく日数です。 *days_until_expiration*は**smallint**で、既定値は 730 (2 年)。 *days_until_expiration* 0 または正の整数にする必要があります。  
  
 [  **@proxy_id =** ] *proxy_id*  
 一意の識別子は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ アカウント。 *proxy_id*は**int**で、既定値は NULL です。 指定した場合*proxy_name* NULL にする必要があります。 取得する*proxy_id*、sysproxies システム テーブルにクエリします。 dc_admin 固定データベース ロールには、プロキシにアクセスする権限が必要です。 詳細については、次を参照してください。 [SQL Server エージェント プロキシを作成する](http://msdn.microsoft.com/library/142e0c55-a8b9-4669-be49-b9dc602d5988)です。  
  
 [  **@proxy_name =** ] '*proxy_name*'  
 プロキシ アカウントの名前です。 *proxy_name*は**sysname**で、既定値は NULL です。 指定した場合*proxy_id* NULL にする必要があります。 取得する*proxy_name*、sysproxies システム テーブルにクエリします。  
  
 [  **@schedule_uid =** ] '*schedule_uid*'  
 スケジュールを参照する GUID です。 *schedule_uid*は**uniqueidentifier**で、既定値は NULL です。 指定した場合*schedule_name* NULL にする必要があります。 取得する*schedule_uid*、sysschedules システム テーブルにクエリします。  
  
 ときに*collection_mode*を 0 に設定されている*schedule_uid*または*schedule_name*指定する必要があります。 ときに*collection_mode*を 1 に設定されている*schedule_uid*または*schedule_name*指定されている場合は無視されます。  
  
 [  **@schedule_name =** ] '*schedule_name*'  
 スケジュールの名前です。 *schedule_name*は**sysname**で、既定値は NULL です。 指定した場合*schedule_uid* NULL にする必要があります。 取得する*schedule_name*、sysschedules システム テーブルにクエリします。  
  
 [  **@logging_level =** ] *logging_level*  
 ログ レベルです。 *logging_level*は**smallint**次の値のいずれかの。  
  
 0 - ログの実行情報と[!INCLUDE[ssIS](../../includes/ssis-md.md)]イベントを追跡します。  
  
-   コレクション セットの開始/停止  
  
-   パッケージの開始/停止  
  
-   エラー情報  
  
 1 - レベル 0 の情報に加えて、以下の情報をログに記録します。  
  
-   実行の統計  
  
-   コレクションの進行状況を継続的に実行します。  
  
-   警告イベント[!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 2 – レベル 1 ログに記録してから詳細なイベント情報[!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 既定値*logging_level*は 1 です。  
  
 [  **@description =** ] '*説明*'  
 コレクション セットの説明です。 *説明*は**nvarchar (4000)**で、既定値は NULL です。  
  
 [  **@collection_set_id =** ] *collection_set_id*  
 コレクション セットの一意なローカル識別子を指定します。 *collection_set_id*は**int**で出力が必要とします。  
  
 [  **@collection_set_uid =** ] '*collection_set_uid*'  
 コレクション セットの場合は GUID です。 *collection_set_uid*は**uniqueidentifier**出力で、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syscollector_create_collection_set は、msdb システム データベースのコンテキストで実行する必要があります。  
  
## <a name="permissions"></a>Permissions  
 このプロシージャを実行するには、(EXECUTE 権限を持つ) dc_admin 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-collection-set-by-using-default-values"></a>A. 既定値を使用してコレクション セットを作成する  
 次の例では、必須パラメーターのみを指定してコレクション セットを作成します。 `@collection_mode`必須ではありませんが (キャッシュ済み)、既定のコレクション モードは、スケジュール ID またはスケジュール名を指定する必要があります。  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
EXECUTE dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 1',  
    @description = N'This is a test collection set that runs in non-cached mode.',  
    @collection_mode = 1,  
    @collection_set_id = @collection_set_id OUTPUT;  
GO  
```  
  
### <a name="b-creating-a-collection-set-by-using-specified-values"></a>B. 値を指定してコレクション セットを作成する  
 次の例では、多数のパラメーターの値を指定してコレクション セットを作成します。  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier;  
SET @collection_set_uid = NEWID();  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 2',  
    @collection_mode = 0,  
    @days_until_expiration = 365,  
    @description = N'This is a test collection set that runs in cached mode.',  
    @logging_level = 2,  
    @schedule_name = N'CollectorSchedule_Every_30min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
```  
  
## <a name="see-also"></a>参照  
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)   
 [ジェネリック T-SQL Query コレクター型を使用するカスタム コレクション セットの作成 &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
