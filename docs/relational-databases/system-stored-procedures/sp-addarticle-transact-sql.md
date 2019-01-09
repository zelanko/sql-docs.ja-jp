---
title: sp_addarticle (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addarticle
- sp_addarticle_TSQL
helpviewer_keywords:
- sp_addarticle
ms.assetid: 0483a157-e403-4fdb-b943-23c1b487bef0
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 732e8a03742e6e2ccc66c158c300222a0701e0c0
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591916"
---
# <a name="spaddarticle-transact-sql"></a>sp_addarticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アーティクルを作成し、パブリケーションに追加します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addarticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
    [ , [ @source_table = ] 'source_table' ]  
    [ , [ @destination_table = ] 'destination_table' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @type = ] 'type' ]   
    [ , [ @filter = ] 'filter' ]   
    [ , [ @sync_object= ] 'sync_object' ]   
        [ , [ @ins_cmd = ] 'ins_cmd' ]   
    [ , [ @del_cmd = ] 'del_cmd' ]   
        [ , [ @upd_cmd = ] 'upd_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @filter_clause = ] 'filter_clause' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @status = ] status ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @sync_object_owner = ] 'sync_object_owner' ]   
    [ , [ @filter_owner = ] 'filter_owner' ]   
    [ , [ @source_object = ] 'source_object' ]   
    [ , [ @artid = ] article_ID  OUTPUT ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @use_default_datatypes = ] use_default_datatypes  
    [ , [ @identityrangemanagementoption = ] identityrangemanagementoption ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @fire_triggers_on_snapshot = ] 'fire_triggers_on_snapshot' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =** ] **'**_パブリケーション_**'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 名前はデータベース内で一意であることが必要です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article =** ] **'**_記事_**'**  
 アーティクルの名前を指定します。 名前はパブリケーション内で一意であることが必要です。 *記事*は**sysname**、既定値はありません。  
  
 [  **@source_table =** ] **'**_source_table_**'**  
 このパラメーターは非推奨とされました。使用して、 *source_object*代わりにします。  
  
 *このパラメーターは、Oracle パブリッシャーに対してはサポートされていません。*  
  
 [  **@destination_table =** ] **'**_destination_table_**'**  
 異なる場合、レプリケーション先 (サブスクリプション) テーブルの名前は、 *source_table*またはストアド プロシージャ。 *destination_table*は**sysname**の既定値は NULL には、つまり*source_table*と等しい*destination_table * *。*  
  
 [  **@vertical_partition =** ] **'**_vertical_partition_**'**  
 テーブル アーティクル上の列フィルター選択を有効または無効にします。 *vertical_partition*は**nchar (5)**、既定値は FALSE。  
  
 **false**垂直方向のフィルター処理がないことを示します、すべての列をパブリッシュします。  
  
 **true**すべての宣言された主キー以外の列、既定値はありません、null 許容の列と一意のキー列を消去します。 使用して列が追加された[sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)します。  
  
 [  **@type =** ] **'**_型_**'**  
 アーティクルの種類を指定します。 *型*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**集計スキーマのみ**|スキーマのみを使用する集計関数。|  
|**func スキーマのみ**|スキーマのみを使用する関数。|  
|**インデックス付きビュー ' logbased '**|ログベースのインデックス付きビュー アーティクルです。 Oracle パブリッシャーに対してはサポートされていません。 この種類のアーティクルに対しては、ベース テーブルを個別にパブリッシュする必要はありません。|  
|**logbased manualboth のインデックス付きビュー**|手動フィルターと手動ビューを使用する、ログベースのインデックス付きビュー アーティクルです。 このオプションは、両方を指定する必要があります*sync_object*と*フィルター*パラメーター。 この種類のアーティクルに対しては、ベース テーブルを個別にパブリッシュする必要はありません。 Oracle パブリッシャーに対してはサポートされていません。|  
|**logbased manualfilter のインデックス付きビュー**|手動フィルターを使用する、ログベースのインデックス付きビュー アーティクルです。 このオプションは、両方を指定する必要があります*sync_object*と*フィルター*パラメーター。 この種類のアーティクルに対しては、ベース テーブルを個別にパブリッシュする必要はありません。 Oracle パブリッシャーに対してはサポートされていません。|  
|**logbased manualview のインデックス付きビュー**|手動ビューを使用する、ログベースのインデックス付きビュー アーティクルです。 このオプションは、指定する必要があります、 *sync_object*パラメーター。 この種類のアーティクルに対しては、ベース テーブルを個別にパブリッシュする必要はありません。 Oracle パブリッシャーに対してはサポートされていません。|  
|**インデックス付きビュー スキーマのみ**|スキーマのみを使用するインデックス付きビュー。 この種類のアーティクルに対しては、ベース テーブルもパブリッシュする必要があります。|  
|**logbased** (既定値)|ログベースのアーティクルです。|  
|**logbased manualboth**|手動フィルターと手動ビューを使用する、ログベースのアーティクルです。 このオプションは、両方を指定する必要があります*sync_object*と*フィルター*パラメーター。 Oracle パブリッシャーに対してはサポートされていません。|  
|**logbased manualfilter**|手動フィルターを使用する、ログベースのアーティクルです。 このオプションは、両方を指定する必要があります*sync_object*と*フィルター*パラメーター。 Oracle パブリッシャーに対してはサポートされていません。|  
|**logbased manualview**|手動ビューを使用する、ログベースのアーティクルです。 このオプションは、指定する必要があります、 *sync_object*パラメーター。 Oracle パブリッシャーに対してはサポートされていません。|  
|**proc exec**|アーティクルのすべてのサブスクライバーにストアド プロシージャの実行をレプリケートします。 Oracle パブリッシャーに対してはサポートされていません。 オプションを使用することをお勧めします。 **serializable proc exec**の代わりに**proc exec**します。 詳細については、「種類のストアド プロシージャ実行アーティクル」セクションを参照してください[トランザクション レプリケーションでの Publishing Stored Procedure Execution](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)します。 変更データ キャプチャが有効な場合は使用できません。|  
|**proc スキーマのみ**|スキーマのみを使用するプロシージャ。 Oracle パブリッシャーに対してはサポートされていません。|  
|**serializable proc exec**|シリアライゼーション可能なトランザクションのコンテキスト内で実行される場合にのみ、ストアド プロシージャの実行をレプリケートします。 Oracle パブリッシャーに対してはサポートされていません。<br /><br /> プロシージャを明示的なトランザクションをレプリケートするプロシージャの実行にも実行する必要があります。|  
|**ビュー スキーマのみ**|スキーマのみを使用するビュー。 Oracle パブリッシャーに対してはサポートされていません。 このオプションを使用する場合は、ベース テーブルもパブリッシュする必要があります。|  
  
 [  **@filter =** ] **'**_フィルター_**'**  
 テーブルの水平方向のフィルター選択に使用する (FOR REPLICATION で作成される) ストアド プロシージャを指定します。 *フィルター*は**nvarchar (386)**、既定値は NULL です。 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)と[sp_articlefilter](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)ビューを作成して、フィルター ストアド プロシージャを手動で実行する必要があります。 NULL 以外を指定した場合は、ストアド プロシージャが手動で作成されるものと見なされるため、フィルター プロシージャは作成されません。  
  
 [  **@sync_object =** ] **'**_sync_object_**'**  
 アーティクルのスナップショットに対応するデータ ファイルの生成に使用されるテーブルまたはビューの名前を指定します。 *sync_object*は**nvarchar (386)**、既定値は NULL です。 NULL の場合、 [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)自動的に出力ファイルを生成するためのビューを作成します。 これには、任意の列を追加した後に発生します[sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)します。 NULL 以外を指定した場合は、ビューが手動で作成されるものと見なされるため、ビューは作成されません。  
  
 [  **@ins_cmd =** ] **'**_ins_cmd_**'**  
 このアーティクルの挿入をレプリケートするときに使用するレプリケーション コマンドの種類を指定します。 *ins_cmd*は**nvarchar (255)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**NONE**|アクションが行われません。|  
|**CALL sp_msins _**<br /> **_テーブル_** (既定値)<br /><br /> - または -<br /><br /> **呼び出し custom_stored_procedure_name**|サブスクライバー側で実行されるストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 *custom_stored_procedure*ユーザーが作成したストアド プロシージャの名前を指定します。 <strong>sp_msins _*テーブル*</strong>の代わりに、変換先テーブルの名前を含む、 *_table*パラメーターの一部です。 ときに*destination_owner*を指定すると、前に対象のテーブル名に付加されます。 たとえば、 **ProductCategory**で所有するテーブル、**運用**、サブスクライバーでスキーマは、パラメーターになります`CALL sp_MSins_ProductionProductCategory`します。 ピア ツー ピア レプリケーション トポロジ内のアーティクル *_table*は GUID 値が付加されます。 指定する*custom_stored_procedure*サブスクライバーの更新はサポートされていません。|  
|**SQL**または NULL|INSERT ステートメントをレプリケートします。 INSERT ステートメントでは、アーティクル内にある、パブリッシュされるすべての列の値が指定されます。 次のコマンドは挿入時にレプリケートされます。<br /><br /> `INSERT INTO <table name> VALUES (c1value, c2value, c3value, ..., cnvalue)`|  
  
 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。  
  
 [  **@del_cmd =**] **'**_del_cmd_**'**  
 このアーティクルの削除をレプリケートするときに使用するレプリケーション コマンドの種類を指定します。 *del_cmd*は**nvarchar (255)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**NONE**|アクションが行われません。|  
|**CALLsp_MSdel_**<br /> **_テーブル_** (既定値)<br /><br /> - または -<br /><br /> **呼び出し custom_stored_procedure_name**|サブスクライバー側で実行されるストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 *custom_stored_procedure*ユーザーが作成したストアド プロシージャの名前を指定します。 <strong>sp_msdel _*テーブル*</strong>の代わりに、変換先テーブルの名前を含む、 *_table*パラメーターの一部です。 ときに*destination_owner*を指定すると、前に対象のテーブル名に付加されます。 たとえば、 **ProductCategory**で所有するテーブル、**運用**、サブスクライバーでスキーマは、パラメーターになります`CALL sp_MSdel_ProductionProductCategory`します。 ピア ツー ピア レプリケーション トポロジ内のアーティクル *_table*は GUID 値が付加されます。 指定する*custom_stored_procedure*サブスクライバーの更新はサポートされていません。|  
|**XCALL sp_msdel _**<br /> **_テーブル_**<br /><br /> - または -<br /><br /> **XCALL custom_stored_procedure_name**|XCALL スタイルのパラメーターを使用してストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 サブスクライバーの更新では、ユーザーが作成したストアド プロシージャを指定できません。|  
|**SQL**または NULL|DELETE ステートメントをレプリケートします。 DELETE ステートメントでは、すべての主キー列の値が指定されます。 次のコマンドは削除時にレプリケートされます。<br /><br /> `DELETE FROM <table name> WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。  
  
 [  **@upd_cmd =**] **'**_upd_cmd_**'**  
 このアーティクルの更新をレプリケートするときに使用するレプリケーション コマンドの種類を指定します。 *upd_cmd*は**nvarchar (255)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**NONE**|アクションが行われません。|  
|**CALL sp_msupd _**<br /> **_テーブル_**<br /><br /> - または -<br /><br /> **呼び出し custom_stored_procedure_name**|サブスクライバー側で実行されるストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。|  
|**MCALL sp_msupd _**<br /> **_テーブル_**<br /><br /> - または -<br /><br /> **MCALL custom_stored_procedure_name**|MCALL スタイルのパラメーターを使用してストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 *custom_stored_procedure*ユーザーが作成したストアド プロシージャの名前を指定します。 <strong>sp_msupd _*テーブル*</strong>の代わりに、変換先テーブルの名前を含む、 *_table*パラメーターの一部です。 ときに*destination_owner*を指定すると、前に対象のテーブル名に付加されます。 たとえば、 **ProductCategory**で所有するテーブル、**運用**、サブスクライバーでスキーマは、パラメーターになります`MCALL sp_MSupd_ProductionProductCategory`します。 ピア ツー ピア レプリケーション トポロジ内のアーティクル *_table*は GUID 値が付加されます。 サブスクライバーの更新では、ユーザーが作成したストアド プロシージャを指定できません。|  
|**SCALL sp_msupd _**<br /> **_テーブル_** (既定値)<br /><br /> - または -<br /><br /> **SCALL custom_stored_procedure_name**|SCALL スタイルのパラメーターを使用してストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 *custom_stored_procedure*ユーザーが作成したストアド プロシージャの名前を指定します。 <strong>sp_msupd _*テーブル*</strong>の代わりに、変換先テーブルの名前を含む、 *_table*パラメーターの一部です。 ときに*destination_owner*を指定すると、前に対象のテーブル名に付加されます。 たとえば、 **ProductCategory**で所有するテーブル、**運用**、サブスクライバーでスキーマは、パラメーターになります`SCALL sp_MSupd_ProductionProductCategory`します。 ピア ツー ピア レプリケーション トポロジ内のアーティクル *_table*は GUID 値が付加されます。 サブスクライバーの更新では、ユーザーが作成したストアド プロシージャを指定できません。|  
|**XCALL sp_msupd _**<br /> **_テーブル_**<br /><br /> - または -<br /><br /> **XCALL custom_stored_procedure_name**|XCALL スタイルのパラメーターを使用してストアド プロシージャを呼び出します。 この方法でレプリケーションを使用する*schema_option*ストアド プロシージャの自動作成を指定するか、アーティクルの各サブスクライバーのレプリケーション先データベースの指定したストアド プロシージャを作成します。 サブスクライバーの更新では、ユーザーが作成したストアド プロシージャを指定できません。|  
|**SQL**または NULL|UPDATE ステートメントをレプリケートします。 UPDATE ステートメントでは、すべての列の値と主キー列の値が指定されます。 次のコマンドは更新時にレプリケートされます。<br /><br /> `UPDATE <table name> SET c1 = c1value, SET c2 = c2value, SET cn = cnvalue WHERE pkc1 = pkc1value AND pkc2 = pkc2value AND pkcn = pkcnvalue`|  
  
> [!NOTE]  
>  構文が CALL 構文、MCALL 構文、SCALL 構文、および XCALL 構文のいずれであるかによって、サブスクライバーに反映されるデータの量が異なります。 CALL 構文では、挿入されたすべての列および削除されたすべての列に関するすべての値が渡されます。 SCALL 構文では、影響を受けた列の値のみが渡されます。 XCALL 構文では、列が変更されているかどうかに関係なく、列の以前の値を含むすべての列の値が渡されます。 詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。  
  
 [  **@creation_script =**] **'**_creation_script_**'**  
 オプションのアーティクル スキーマ スクリプトのパスと名前を指定します。このスクリプトは、サブスクリプション データベースでアーティクルを作成する場合に使用されます。 *creation_script*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@description =**] **'**_説明_**'**  
 アーティクルの説明エントリを指定します。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@pre_creation_cmd =**] **'**_pre_creation_cmd_**'**  
 このアーティクルのスナップショットを適用したときに、サブスクライバー側で同じ名前の既存のオブジェクトが検出された場合に取る措置を指定します。 *pre_creation_cmd*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**[なし]**|コマンドを使用しません。|  
|**delete**|スナップショットを適用する前に、レプリケーション先テーブルからデータを削除します。 アーティクルが行方向にフィルター選択されている場合、フィルターによって指定された列のデータのみが削除されます。 行フィルターが定義されている場合は、Oracle パブリッシャーに対してはサポートされません。|  
|**drop** (既定値)|レプリケーション先テーブルを破棄します。|  
|**truncate**|レプリケーション先テーブルを切り捨てます。 ODBC サブスクライバーまたは OLE DB サブスクライバーに対しては無効です。|  
  
 [  **@filter_clause=**] **'**_filter_clause_**'**  
 行フィルターを定義する制限句 (WHERE) を指定します。 制限句を入力する場合は、WHERE キーワードを省略します。 *filter_clause*は**ntext**、既定値は NULL です。 詳細については、「[パブリッシュされたデータのフィルター選択](../../relational-databases/replication/publish/filter-published-data.md)」を参照してください。  
  
 [  **@schema_option =**] *schema_option*  
 指定したアーティクルに対するスキーマ生成オプションのビットマスクを指定します。 *schema_option*は**binary (8)**、でき、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)これらの値の 1 つ以上の製品。  
  
> [!NOTE]  
>  この値が NULL の場合は、他のアーティクルのプロパティに応じて、アーティクルの有効なスキーマ オプションが自動生成されます。 **スキーマ オプションの既定の**「解説」で指定されたテーブル アーティクルの種類とレプリケーションの種類の組み合わせに基づいて選択される値を示しています。  
  
|値|説明|  
|-----------|-----------------|  
|**0x00**|スナップショット エージェントによるスクリプト作成を無効にしを使用して*creation_script*します。|  
|**0x01**|オブジェクト作成スクリプト (CREATE TABLE、CREATE PROCEDURE など) を生成します。 ストアド プロシージャ アーティクルの既定値です。|  
|**0x02**|定義されている場合、アーティクルの変更を反映するストアド プロシージャを生成します。|  
|**0x04**|ID 列のスクリプトが IDENTITY プロパティを使用して作成されます。|  
|**0x08**|レプリケート**タイムスタンプ**列。 ない場合、**タイムスタンプ**として列をレプリケート**バイナリ**します。|  
|**0x10**|対応するクラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと一意の制約が既に定義されている場合は、これらに関連するインデックスが生成されます。|  
|**0x20**|サブスクライバーでユーザー定義データ型 (UDT) を基本データ型に変換します。 UDT 列に CHECK 制約または DEFAULT 制約があるときに、UDT 列が主キーの一部になっている場合、または計算列で UDT 列が参照されている場合、このオプションは使用できません。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x40**|対応する非クラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと一意の制約が既に定義されている場合は、これらに関連するインデックスが生成されます。|  
|**0x80**|主キー制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x100**|定義されている場合、テーブル アーティクル上のユーザー トリガーをレプリケートします。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x200**|外部キー制約をレプリケートします。 参照するテーブルがパブリケーションの一部でない場合は、パブリッシュされたテーブルのすべての外部キー制約がレプリケートされるわけではありません。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x400**|CHECK 制約をレプリケートします。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x800**|既定値をレプリケートします。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x1000**|列レベルの照合順序をレプリケートします。<br /><br /> **注:** 大文字と小文字を区別する比較を有効にするには、このオプションを Oracle パブリッシャーに対して設定する必要があります。|  
|**0x2000**|パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**0x4000**|UNIQUE 制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x8000**|このオプションは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] パブリッシャーでは無効です。|  
|**0x10000**|CHECK 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
|**0x20000**|FOREIGN KEY 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
|**0x40000**|パーティション テーブルまたはインデックスに関連付けられているファイル グループをレプリケートします。|  
|**これに対して、0x80000**|パーティション テーブルのパーティション構成をレプリケートします。|  
|**0x100000**|パーティション インデックスのパーティション構成をレプリケートします。|  
|**0x200000**|テーブルの統計をレプリケートします。|  
|**0x400000**|既定のバインドです。|  
|**0x800000**|ルールのバインドです。|  
|**0x1000000**|フルテキスト インデックスです。|  
|**0x2000000**|バインドされた XML スキーマ コレクション**xml**列はレプリケートされません。|  
|**0x4000000**|インデックスをレプリケート**xml**列。|  
|**0x8000000**|サブスクライバーにまだ存在しないスキーマを作成します。|  
|**0x10000000**|変換します**xml**列**ntext**サブスクライバーにします。|  
|**0x20000000**|変換の大きなオブジェクトのデータ型 (**nvarchar (max)**、 **varchar (max)**、および**varbinary (max)**) で導入された[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]でサポートされているデータ型[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|アクセス許可をレプリケートします。|  
|**0x80000000**|パブリケーションの一部ではない任意のオブジェクトに対する依存関係を削除しようとしてください。|  
|**0x100000000**|このオプションを使用して、指定されている場合は、FILESTREAM 属性をレプリケートする**varbinary (max)** 列。 テーブルを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] サブスクライバーにレプリケートする場合は、このオプションを指定しないでください。 FILESTREAM 列を持つテーブルをレプリケート[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーがサポートされていません、このスキーマ オプションを設定する方法に関係なく、します。<br /><br /> 関連するオプションを参照してください。 **0x800000000**します。|  
|**0x200000000**|日付と時刻のデータ型に変換 (**日付**、**時間**、 **datetimeoffset**、および**datetime2**) で導入された[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]データ以前のバージョンでサポートされている種類[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**0x400000000**|データとインデックスの圧縮オプションをレプリケートします。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。|  
|**0x800000000**|このオプションを設定すると、サブスクライバーの独自のファイル グループに FILESTREAM データを格納できます。 このオプションが設定されていない場合、FILESTREAM データは既定のファイル グループに格納されます。 レプリケーションではファイル グループは作成されないので、このオプションを設定する場合は、サブスクライバーでスナップショットを適用する前にファイル グループを作成しておく必要があります。 スナップショットを適用する前に、オブジェクトを作成する方法の詳細については、次を参照してください。[前にスクリプトを実行し、後のスナップショットが適用される](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)します。<br /><br /> 関連するオプションを参照してください。 **0x100000000**します。|  
|**0x1000000000**|共通言語ランタイム (CLR) ユーザー定義型 (Udt) 8000 バイトを超えるに変換します**varbinary (max)** を実行しているサブスクライバーに UDT 型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。|  
|**0x2000000000**|変換、 **hierarchyid**のデータ型**varbinary (max)** ように型の列**hierarchyid**実行しているサブスクライバーにレプリケートできる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。 使用する方法の詳細についての**hierarchyid**レプリケートされたテーブル内の列を参照してください[hierarchyid &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)します。|  
|**0x4000000000**|テーブルのフィルター選択されたインデックスをレプリケートします。 フィルター選択されたインデックスの詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)します。|  
|**0x8000000000**|変換、 **geography**と**geometry**データ型を**varbinary (max)** を実行しているサブスクライバーにこれらの型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|型の列にインデックスをレプリケート**geography**と**geometry**します。|  
|**0x20000000000**|列の SPARSE 属性をレプリケートします。 この属性の詳細については、次を参照してください。[スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)します。|  
|**0x40000000000**|サブスクライバーのメモリ最適化テーブルを作成するには、スナップショット エージェントによるスクリプト作成を有効にします。|  
|**0x80000000000**|アーティクルのメモリ最適化非クラスター化インデックスをクラスター化インデックスを変換します。|  
|**0x400000000000**|テーブルの非クラスター化列ストア インデックスをレプリケートします。|  
|**0x800000000000**|テーブルで flitered 非クラスター化列ストア インデックスをレプリケートします。|  
|NULL|レプリケーションが自動的に設定*schema_option*既定値に、この値が他のアーティクルのプロパティに依存します。 「解説」に記載されている「既定のスキーマ オプション」の表は、アーティクルの種類とレプリケーションの種類に基づいた既定のスキーマ オプションを示します。<br /><br /> 既定値以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーションは**0x050D3**します。|  
  
 すべて*schema_option*値は、レプリケーションのすべての種類およびアーティクルの種類に有効です。 **有効なスキーマ オプション**「解説」セクションの表は、アーティクルの種類とレプリケーション種類の組み合わせに基づいて選択できる有効なスキーマ オプションを示しています。  
  
 [  **@destination_owner =**] **'**_destination_owner_**'**  
 レプリケーション先オブジェクトの所有者の名前を指定します。 *destination_owner*は**sysname**、既定値は NULL です。 ときに*destination_owner*が指定されていない、次の規則に基づいて自動的に所有者を指定します。  
  
|条件|対象オブジェクトの所有者|  
|---------------|------------------------------|  
|パブリケーションはネイティブ モードの一括コピーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーのみをサポートする初期スナップショットを生成します。|値の既定値は*source_owner*します。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーからパブリッシュされます。|既定では、レプリケーション先データベースの所有者に設定されます。|  
|パブリケーションはキャラクター モードの一括コピーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーをサポートする初期スナップショットを生成します。|割り当てられていません。|  
  
 非をサポートする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー、 *destination_owner* NULL にする必要があります。  
  
 [  **@status=**]*状態*  
 アーティクルがアクティブであるかどうか、および変更がどのように反映されるかについての追加オプションを指定します。 *ステータス*は**tinyint**、でき、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)これらの値の 1 つ以上の製品です。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|アーティクルがアクティブです。|  
|**8**|INSERT ステートメントに列名を含めます。|  
|**16** (既定値)|パラメーター化されたステートメントを使用します。|  
|**24**|INSERT ステートメントに列名を含めて、パラメーター化されたステートメントを使用します。|  
|**64**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 たとえば、パラメーター化されたステートメントを使用するアクティブなアーティクルの場合、この列の値は 17 になります。 値**0**アーティクルがアクティブでないと、追加のプロパティが定義されていないことを意味します。  
  
 [  **@source_owner =**] **'**_source_owner_**'**  
 ソース オブジェクトの所有者を指定します。 *source_owner*は**sysname**、既定値は NULL です。 *source_owner* Oracle パブリッシャーに対して指定する必要があります。  
  
 [  **@sync_object_owner =**] **'**_sync_object_owner_**'**  
 パブリッシュされたアーティクルを定義するビューの所有者を指定します。 *sync_object_owner*は**sysname**、既定値は NULL です。  
  
 [  **@filter_owner =**] **'**_filter_owner_**'**  
 フィルターの所有者を指定します。 *filter_owner*は**sysname**、既定値は NULL です。  
  
 [  **@source_object =**] **'**_source_object_**'**  
 パブリッシュされるデータベース オブジェクトを指定します。 *source_object*は**sysname**、既定値は NULL です。 場合*source_table*が null の場合、 *source_object* NULL にすることはできません *。source_object*の代わりに使用する必要があります*source_table*します。 スナップショット パブリケーションまたはトランザクション レプリケーションを使用してパブリッシュできるオブジェクトの種類の詳細については、次を参照してください。[発行データおよびデータベース オブジェクト](../../relational-databases/replication/publish/publish-data-and-database-objects.md)します。  
  
 [  **@artid =** ]_コ_**出力**  
 新しいアーティクルのアーティクル ID です。 *コ*は**int**既定値は null には、出力パラメーター。  
  
 [  **@auto_identity_range =** ] **'**_auto_identity_range_**'**  
 パブリケーションの作成時、パブリケーションでの自動 ID 範囲処理を有効または無効にします。 *auto_identity_range*は**nvarchar (5)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**true**|自動 ID 範囲処理を有効にします。|  
|**false**|自動 ID 範囲処理を無効にします。|  
|NULL(default)|Id 範囲処理を定めた*identityrangemanagementoption*します。|  
  
> [!NOTE]  
>  *auto_identity_range*は非推奨し、旧バージョンとの互換性を保つのために提供されます。 使用する必要があります*identityrangemanagementoption* id 範囲管理オプションを指定するためです。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 [  **@pub_identity_range =** ] *identity_range*  
 場合、アーティクルはパブリッシャーの範囲のサイズを制御*identityrangemanagementoption*設定**自動**または*auto_identity_range*に設定**は true。**. *identity_range*は**bigint**、既定値は NULL です。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **@identity_range =** ] *identity_range*  
 場合、アーティクルは、サブスクライバーの範囲のサイズを制御*identityrangemanagementoption*設定**自動**または*auto_identity_range*に設定**は true。**. *identity_range*は**bigint**、既定値は NULL です。 ときに使用される*auto_identity_range*に設定されている**true**します。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **@threshold =** ]*しきい値*  
 ディストリビューション エージェントがどの時点で新しい ID 範囲を割り当てるかを制御するパーセンテージの値を指定します。 値の比率が指定されている場合*しきい値*はディストリビューション エージェント、新しい id 範囲を作成します。 *しきい値*は**bigint**、既定値は NULL です。 ときに使用される*identityrangemanagementoption*に設定されている**自動**または*auto_identity_range*に設定されている**true**します。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [ **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は 0。  
  
 **0**アーティクルの追加も無効になるスナップショットは発生しませんを指定します。 変更に新しいスナップショットが必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  
 **1**追加アーティクルがスナップショットが無効であることになることが、新しいスナップショットをする必要があるサブスクリプションが存在しない場合、obsolete としてマーク済みである既存のスナップショットと、新しいスナップショットを生成するためのアクセス許可を提供するを指定します。  
  
 [  **@use_default_datatypes =** ] *use_default_datatypes*  
 Oracle パブリッシャーからアーティクルをパブリッシュするときに既定の列のデータ型マッピングが使用されるかどうかを示します。 *use_default_datatypes*ビットは、既定値は 1 です。  
  
 **1** = 既定のアーティクル列マッピングが使用されます。 既定のデータ型マッピングを実行して表示できる[sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)します。  
  
 **0** = カスタム アーティクル列のマッピングが定義されている、ため[sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)がによって呼び出されなかった**sp_addarticle**します。  
  
 ときに*use_default_datatypes*に設定されている**0**、実行する必要があります[sp_changearticlecolumndatatype](../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md)既定から変更されている列マッピングごとに 1 回です。 実行する必要がありますすべてのカスタム列マッピングを定義したら[sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。  
  
> [!NOTE]  
>  このパラメーターは、Oracle パブリッシャーに対してのみ使用する必要があります。 設定*use_default_datatypes*に**0**の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーには、エラーが生成されます。  
  
 [  **@identityrangemanagementoption =** ] *identityrangemanagementoption*  
 アーティクルに対する ID 範囲の管理がどのように処理されるかを指定します。 *identityrangemanagementoption*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**[なし]**|明示的な ID 範囲の管理は行われません。 このオプションは、旧バージョンの SQL Server との互換性を維持する目的でのみ使用することをお勧めします。 ピア レプリケーションに対しては使用できません。|  
|**手動**|NOT FOR REPLICATION を使用して手動による ID 範囲処理を有効にしている ID 列にマークを付けます。|  
|**自動**|ID 範囲の自動管理を指定します。|  
|NULL(default)|既定値は**none**ときの値*auto_identity_range*でない**true**します。 既定値は**手動**ピア ツー ピア トポロジの既定の (*auto_identity_range*は無視されます)。|  
  
 旧バージョンとの互換性のためときの値*identityrangemanagementoption* null の場合の値は、 *auto_identity_range*がチェックされます。 ただし、場合の値*identityrangemanagementoption* null の場合、次の値でない*auto_identity_range*は無視されます。  
  
 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 [  **@publisher =** ] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*にアーティクルを追加するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@fire_triggers_on_snapshot =** ] **'**_fire_triggers_on_snapshot_**'**  
 初期スナップショットが適用されたときに、レプリケートされたユーザー トリガーが実行されるかどうかを示します。 *fire_triggers_on_snapshot*は**nvarchar (5)**、既定値は FALSE。 **true**スナップショットが適用されるときに、レプリケートされたテーブル上でユーザー トリガーが実行されることを意味します。 トリガーをレプリケートするためのビットマスク値*schema_option*値を含める必要があります**0x100**します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addarticle**スナップショット レプリケーションまたはトランザクション レプリケーションで使用されます。  
  
 既定では、列データ型がレプリケーションによってサポートされていない場合は、レプリケーションによってソース テーブル内の列がパブリッシュされることはありません。 実行する必要があります、このような列をパブリッシュする必要がある場合[sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)列を追加します。  
  
 ピア ツー ピア トランザクション レプリケーションをサポートしているパブリケーションにアーティクルを追加するときは、次の制限が適用されます。  
  
-   パラメーター化されたステートメントをすべてのログベースのアーティクルに対して指定する必要があります。 含める必要があります**16**で、*状態*値。  
  
-   レプリケーション先テーブルの名前と所有者は、ソース テーブルと一致する必要があります。  
  
-   アーティクルは、行方向または列方向にフィルター選択することはできません。  
  
-   自動 ID 範囲管理はサポートされていません。 マニュアルの値を指定する必要があります*identityrangemanagementoption*します。  
  
-   場合、**タイムスタンプ**テーブルの列が存在するに 0x08 を含める必要があります*schema_option*として列をレプリケートする**タイムスタンプ**します。  
  
-   値**SQL**は指定できません*ins_cmd*、 *upd_cmd*、および*del_cmd*します。  
  
 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 オブジェクトを発行するときに、その定義がサブスクライバーにコピーされます。 他の 1 つ以上のオブジェクトに依存しているデータベース オブジェクトをパブリッシュする場合は、参照されるオブジェクトをすべてパブリッシュする必要があります。 たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。  
  
 場合*vertical_partition*に設定されている**true**、 **sp_addarticle**までビューの作成を延期[sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) (後に呼び出されます最後の[sp_articlecolumn](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)が追加されます)。  
  
 パブリケーションのサブスクリプションと、パブリッシュされたテーブルの更新が許可する場合、必要はありません、 **uniqueidentifier**列、 **sp_addarticle**を追加、**一意識別子**列テーブルに自動的にします。  
  
 インスタンスではないサブスクライバーにレプリケートするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](異種レプリケーション) のみ[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントはサポートされて**挿入**、 **UPDATE**、および**削除**コマンド。  
  
 ログ リーダー エージェントを実行している場合、アーティクルをピア ツー ピア パブリケーションに追加すると、ログ リーダー エージェントと、アーティクルを追加するプロセスとの間にデッドロックが発生する場合があります。 この問題を回避するには、アーティクルをピア ツー ピア パブリケーションに追加する前に、レプリケーション モニターを使用して、アーティクルを追加するノードのログ リーダー エージェントを停止します。 アーティクルを追加した後で、ログ リーダー エージェントを再起動します。  
  
 設定するときに`@del_cmd = 'NONE'`または`@ins_cmd = 'NONE'`の伝達**更新**コマンドは、範囲指定された更新が発生した場合、これらのコマンドを送信しないことにより影響も可能性があります。 範囲指定された更新は、サブスクライバーに対する DELETE/INSERT ペアとしてレプリケートするパブリッシャーの UPDATE ステートメントの種類です。  
  
## <a name="default-schema-options"></a>既定のスキーマ オプション  
 次の表は、レプリケーションによって設定される場合は既定値を示します*schema_options*がこの値が (上部に表示される) レプリケーションの種類およびアーティクルの種類 (最初の列 1) に依存する場所、ユーザーが指定されていません。  
  
|アーティクルの種類|レプリケーションの種類||  
|------------------|----------------------|------|  
||トランザクション|スナップショット|  
|**集計スキーマのみ**|**0x01**|**0x01**|  
|**func スキーマのみ**|**0x01**|**0x01**|  
|**インデックス付きビュー スキーマのみ**|**0x01**|**0x01**|  
|**インデックス付きビュー ' logbased '**|**0x30F3**|**0x3071**|  
|**インデックス付きビューの対数の底 manualboth**|**0x30F3**|**0x3071**|  
|**logbased manualfilter のインデックス付きビュー**|**0x30F3**|**0x3071**|  
|**logbased manualview のインデックス付きビュー**|**0x30F3**|**0x3071**|  
|**logbased**|**0x30F3**|**0x3071**|  
|**logbased manualfilter**|**0x30F3**|**0x3071**|  
|**logbased manualview**|**0x30F3**|**0x3071**|  
|**proc exec**|**0x01**|**0x01**|  
|**proc スキーマのみ**|**0x01**|**0x01**|  
|**serializable proc exec**|**0x01**|**0x01**|  
|**ビュー スキーマのみ**|**0x01**|**0x01**|  
  
> [!NOTE]
>  パブリケーションがキュー更新を有効になっている場合、 *schema_option* @property **0x80**の表に示す既定値に追加されます。 既定の*schema_option*以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーションは**0x050D3**します。  
  
## <a name="valid-schema-options"></a>有効なスキーマ オプション  
 この表に指定できる値*schema_option* (上部に表示される) レプリケーションの種類およびアーティクルの種類 (最初の列 1) に基づいています。  
  
|アーティクルの種類|レプリケーションの種類||  
|------------------|----------------------|------|  
||トランザクション|スナップショット|  
|**logbased**|すべてのオプション|すべてのオプションが**0x02**|  
|**logbased manualfilter**|すべてのオプション|すべてのオプションが**0x02**|  
|**logbased manualview**|すべてのオプション|すべてのオプションが**0x02**|  
|**インデックス付きビュー ' logbased '**|すべてのオプション|すべてのオプションが**0x02**|  
|**logbased manualfilter のインデックス付きビュー**|すべてのオプション|すべてのオプションが**0x02**|  
|**logbased manualview のインデックス付きビュー**|すべてのオプション|すべてのオプションが**0x02**|  
|**インデックス付きビューの対数の底 manualboth**|すべてのオプション|すべてのオプションが**0x02**|  
|**proc exec**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|  
|**serializable proc exec**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|  
|**proc スキーマのみ**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|  
|**ビュー スキーマのみ**|**0x01**、 **0x010**、 **0x020**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x100000**、 **0x200000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x010**、 **0x020**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x100000**、 **0x200000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x40000000**、および**0x80000000**|  
|**func スキーマのみ**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x20**、 **0x2000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x10000000**、 **0x20000000**、 **0x40000000**、および**0x80000000**|  
|**インデックス付きビュー スキーマのみ**|**0x01**、 **0x010**、 **0x020**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x100000**、 **0x200000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x40000000**、および**0x80000000**|**0x01**、 **0x010**、 **0x020**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x100000**、 **0x200000**、 **0x400000**、 **0x800000**、 **0x2000000**、 **0x8000000**、 **0x40000000**、および**0x80000000**|  
  
> [!NOTE]
>  更新パブリケーションのキューに置かれた場合、 *schema_option*値**0x8000**と**0x80**有効にする必要があります。 サポートされている*schema_option*値以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーションは。**0x01**、 **0x02**、 **0x10**、 **0x40**、 **0x80**、 **0x1000**、 **0x4000**と**0X8000**します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-addarticle-transact-sql_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addarticle**します。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
