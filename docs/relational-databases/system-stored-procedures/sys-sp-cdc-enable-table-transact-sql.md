---
title: sys.sp_cdc_enable_table (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_enable_table_TSQL
- sp_cdc_enable_table_TSQL
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- sys.sp_cdc_enable_table
- sp_cdc_enable_table
ms.assetid: 26150c09-2dca-46ad-bb01-3cb3165bcc5d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2b234aba562c095d2861bddec5310cf321b5d331
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591066"
---
# <a name="sysspcdcenabletable-transact-sql"></a>sys.sp_cdc_enable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内の指定したソース テーブルを対象に変更データ キャプチャを有効にします。 テーブルに対して変更データ キャプチャを有効にすると、テーブルに適用された各データ操作言語 (DML) の操作に関するレコードが、トランザクション ログに書き込まれます。 変更データ キャプチャ プロセスは、この情報をログから取得し、一連の関数を使用してアクセスできる変更テーブルに書き込みます。  
  
 変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_enable_table   
  [ @source_schema = ] 'source_schema',   
  [ @source_name = ] 'source_name' ,  [,[ @capture_instance = ] 'capture_instance' ]  
  [,[ @supports_net_changes = ] supports_net_changes ]  
  , [ @role_name = ] 'role_name'  
  [,[ @index_name = ] 'index_name' ]  
  [,[ @captured_column_list = ] 'captured_column_list' ]  
  [,[ @filegroup_name = ] 'filegroup_name' ]  
  [,[ @allow_partition_switch = ] 'allow_partition_switch' ]  
  [;]  
```  
  
## <a name="arguments"></a>引数  
 [  **@source_schema =** ] **'**_source_schema_**'**  
 ソース テーブルが属するスキーマの名前です。 *source_schema*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [  **@source_name =** ] **'**_source_name_**'**  
 変更データ キャプチャを有効にするソース テーブルの名前です。 *source_name*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 *source_name*現在のデータベースに存在する必要があります。 内のテーブル、 **cdc**スキーマは変更データ キャプチャを有効にすることはできません。  
  
 [  **@role_name =** ] **'**_role_name_**'**  
 変更データへのアクセスに使用するデータベース ロールの名前です。 *role_name*は**sysname**と指定する必要があります。 明示的に NULL に設定した場合、変更データへのアクセスを制限する際にゲーティング ロールは使用されません。  
  
 指定されたロールが現在存在する場合は、そのロールが使用されます。 指定されたロールが存在しない場合は、その名前でデータベース ロールの作成が試行されます。 ロール名を表す文字列の右側の空白文字は、ロールの作成前に切り捨てられます。 呼び出し元に、対象のデータベース内にロールを作成する権限がない場合、このストアド プロシージャ操作は失敗します。  
  
 [  **@capture_instance =** ] **'**_capture_instance_**'**  
 インスタンス固有の変更データ キャプチャ オブジェクトを識別するために使用されるキャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname** NULL にすることはできません。  
  
 名前が、ソース スキーマ名の形式でソース テーブル名から派生した指定しない場合、 *schemaname_sourcename*します。 *capture_instance* 100 文字を超えることはできませんし、データベース内で一意である必要があります。 指定されたか、派生*capture_instance*文字列の右側にある空白は切り捨てられます。  
  
 ソース テーブルには、最大 2 つのキャプチャ インスタンスを割り当てることができます。 詳細については、「 [sys.sp_cdc_help_change_data_capture &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)します。  
  
 [  **@supports_net_changes =** ] *supports_net_changes*  
 差分変更クエリのサポートをこのキャプチャ インスタンスで有効にするかどうかを示します。 *supports_net_changes*は**ビット**、既定値は、テーブルに主キーまたはテーブルに一意のインデックスを使用して識別されている場合は 1、@index_nameパラメーター。 それ以外の場合、既定値は 0 になります。  
  
 0 の場合は、すべての変更のクエリをサポートする関数のみが生成されます。  
  
 1 の場合は、差分変更のクエリに必要な関数も生成されます。  
  
 場合*supports_net_changes*を 1 に設定されている*index_name*指定する必要がありますか、ソース テーブルは主キーが定義されている必要があります。  
  
 [  **@index_name =** ] **'**_index_name_'  
 ソース テーブル内の行を一意に識別するために使用する、一意のインデックスの名前を指定します。 *index_name*は**sysname** NULL にすることができます。 指定した場合*index_name*ソース テーブルに一意のインデックスを有効にする必要があります。 場合*index_name*インデックス列よりも優先、定義された主キー列、テーブルの一意の行識別子として指定します。  
  
 [  **@captured_column_list =** ] **'**_captured_column_list_**'**  
 変更テーブルに追加するソース テーブルの列を指定します。 *captured_column_list*は**nvarchar (max)** NULL にすることができます。 NULL の場合、すべての列が変更テーブルに追加されます。  
  
 列名は、ソース テーブル内の有効な列であることが必要です。 主キー インデックスで定義された列または列によって参照されるインデックスで定義されている*index_name*含める必要があります。  
  
 *captured_column_list*は列名のコンマ区切りのリスト。 個々の列名は、二重引用符 ("") または角かっこ ([]) で囲んで指定することもできます。 列名そのものにコンマが含まれる場合は、列名をこれらの記号で囲んで指定する必要があります。  
  
 *captured_column_list*次の予約済みの列名を含めることはできません: **_ _ $start_lsn**、 **_ _ $end_lsn**、 **_ _ $$seqval**、 **_ _ $操作**、および **_ _ $update_mask**します。  
  
 [  **@filegroup_name =** ] **'**_filegroup_name_**'**  
 キャプチャ インスタンスに対して作成された変更テーブルに使用するファイル グループを指定します。 *filegroup_name*は**sysname** NULL にすることができます。 指定した場合*filegroup_name*現在のデータベースを定義する必要があります。 NULL の場合は、既定のファイル グループが使用されます。  
  
 変更データ キャプチャの変更テーブル用に、別個のファイル グループを作成することをお勧めします。  
  
 [  **@allow_partition_switch=** ] **'**_allow_partition_switch_**'**  
 変更データ キャプチャが有効であるテーブルに対して ALTER TABLE の SWITCH PARTITION コマンドを実行できるかどうかを指定します。 *allow_partition_switch*は**ビット**、既定値は 1 です。  
  
 非パーティション テーブルの場合、切り替え設定は常に 1 になり、実際の設定は無視されます。 非パーティション テーブルで切り替え設定を明示的に 0 に設定すると、切り替え設定が無視されたことを示す警告 22857 が生成されます。 パーティション テーブルで切り替え設定を明示的に 0 に設定すると、ソース テーブルに対するパーティションの切り替え操作が許可されなくなることを示す警告 22356 が生成されます。 切り替え設定を明示的に 1 に設定するか、既定値の 1 をそのまま使用し、有効なテーブルがパーティション分割される場合は、パーティションの切り替えがブロックされないことを示す警告 22855 が生成されます。 パーティションの切り替えが行われた場合、切り替えによって生じた変更は変更データ キャプチャによって追跡されません。 このため、変更データの使用時にデータの不整合が生じる可能性があります。  
  
> [!IMPORTANT]  
>  SWITCH PARTITION はメタデータの操作ですが、データ変更を伴います。 この操作に関連するデータ変更は、変更データ キャプチャの変更テーブルにはキャプチャされません。 3 つのパーティションがあるテーブルに対して変更が加えられるとします。 キャプチャ プロセスでは、このテーブルに対して実行されるユーザーの挿入操作、更新操作、および削除操作を追跡します。 ただし、パーティションが別のテーブルに切り替えられた場合 (一括削除の実行など)、この操作の一部として移動された行は、変更テーブルには削除された行としてキャプチャされません。 同様に、既に行が作成されている新しいパーティションがテーブルに追加された場合、これらの行は変更テーブルには反映されません。 このため、変更がアプリケーションで使用され、変更先に適用されると、データの不整合が生じる可能性があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 テーブルに対して変更データ キャプチャを有効にする前に、データベースに対して変更データ キャプチャを有効にする必要があります。 データベースで変更データ キャプチャが有効かどうかを確認するのには、クエリ、 **is_cdc_enabled**内の列、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。 データベースを有効にするには使用、 [sys.sp_cdc_enable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)ストアド プロシージャ。  
  
 テーブルに対して変更データ キャプチャを有効にすると、変更テーブルと 1 つまたは 2 つのクエリ関数が生成されます。 変更テーブルは、キャプチャ プロセスによってトランザクション ログから抽出されたソース テーブルの変更に関するリポジトリとして機能します。 クエリ関数は、変更テーブルからデータを抽出するために使用されます。 これらの関数の名前がから派生した、 *capture_instance*次の方法でパラメーター。  
  
-   すべての変更関数: **cdc.fn_cdc_get_all_changes_ < capture_instance >**  
  
-   差分変更関数: **cdc.fn_cdc_get_net_changes_ < capture_instance >**  
  
 **sys.sp_cdc_enable_table**ソース テーブルが変更データ キャプチャを有効にするデータベース内の最初のテーブルおよびデータベースのトランザクション パブリケーションが存在しない場合も、データベースのキャプチャとクリーンアップ ジョブを作成します。 設定、 **is_tracked_by_cdc**内の列、 [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)カタログ ビューを 1 にします。  
  
> [!NOTE]  
>  テーブルで変更データ キャプチャが有効になっている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されている必要はありません。 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されていない場合、キャプチャ プロセスによってトランザクション ログの処理および変更テーブルへのエントリの書き込みが行われることはありません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-enabling-change-data-capture-by-specifying-only-required-parameters"></a>A. 必須のパラメーターのみを指定して変更データ キャプチャを有効にする  
 次の例では、`HumanResources.Employee` テーブルに対して変更データ キャプチャを有効にします。 指定されているのは、必須のパラメーターだけです。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Employee'  
  , @role_name = N'cdc_Admin';  
GO  
```  
  
### <a name="b-enabling-change-data-capture-by-specifying-additional-optional-parameters"></a>B. 追加のオプション パラメーターを指定して変更データ キャプチャを有効にする  
 次の例では、`HumanResources.Department` テーブルに対して変更データ キャプチャを有効にします。 `@allow_partition_switch` 以外のすべてのパラメーターが指定されています。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_enable_table  
    @source_schema = N'HumanResources'  
  , @source_name = N'Department'  
  , @role_name = N'cdc_admin'  
  , @capture_instance = N'HR_Department'   
  , @supports_net_changes = 1  
  , @index_name = N'AK_Department_Name'   
  , @captured_column_list = N'DepartmentID, Name, GroupName'   
  , @filegroup_name = N'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_disable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)   
 [sys.sp_cdc_help_change_data_capture &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)  
  
  
