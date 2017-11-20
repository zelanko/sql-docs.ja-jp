---
title: "catalog.add_data_tap_by_guid |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ed9d7fa3-61a1-4e21-ba43-1ead7dfc74eb
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9bd4ecb4a6a419f1965a349d46d16d764dd83708
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatapbyguid"></a>catalog.add_data_tap_by_guid
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  パッケージ データ フロー内の特定のデータ フロー パスに、実行のインスタンスのデータ タップを追加します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog add_data_tap_by_guid [ @execution_id = ] execution_id  
, [ @dataflow_task_guid = ] dataflow_task_guid   
, [ @dataflow_path_id_string = ] dataflow_path_id_string  
, [ @data_filename = ] data_filename  
, [ @max_rows = ] max_rows  
, [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id =] *execution_id*  
 パッケージを含む実行の実行 ID。 *Execution_id*は、 **bigint**です。  
  
 [ @dataflow_task_guid =] *dataflow_task_guid*  
 タップするデータ フロー パスを含むパッケージ内のデータ タスク フローの ID。 *Dataflow_task_guid*は、**uniqueidentifier**です。  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 データ フロー パスの識別文字列。 パスは、2 つのデータ フロー コンポーネントを連結します。 **IdentificationString**パスのプロパティの文字列を指定します。  
  
 内で識別文字列を検索する[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]クリックして 2 つのデータ フロー コンポーネント間のパスを右クリックして**プロパティ**です。 **IdentificationString**プロパティに表示されて、**プロパティ**ウィンドウです。  
  
 *Dataflow_path_id_string*は、 **nvarchar (4000)**です。  
  
 [ @data_filename =] *data_filename*  
 タップされたデータを格納するファイルの名前。 データ フロー タスクが Foreach Loop コンテナーまたは For Loop コンテナーの中で実行される場合、ループの反復ごとにタップされたデータが個別のファイルに格納されます。 各ファイルの先頭には、反復に対応する番号が付けられます。 データ タップ ファイルは、フォルダーに書き込まれます"*\<SQL Server のインストール フォルダー >*\130\DTS\\"です。 *Data_filename*は、 **nvarchar (4000)**です。  
  
 [ @max_rows =] max_rows  
 データ タップ中にキャプチャされる行の数。 この値が指定されていない場合は、すべての行がキャプチャされます。 Max_rows は、 **int**です。  
  
 [ @data_tap_id =] *data_tap_id*  
 データ タップの ID。 *Data_tap_id*は、 **bigint**です。  
  
## <a name="example"></a>例  
 次の例では、データ タップがデータ フロー パスで作成された`Paths[SRC DimDCVentor.OLE DB Source Output]`で、データ フロー タスク`{D978A2E4-E05D-4374-9B05-50178A8817E8}`です。 タップされたデータは、DCVendorOutput.csv ファイルに格納されます。  
  
```sql
exec catalog.add_data_tap_by_guid   @execution_id,   
'{D978A2E4-E05D-4374-9B05-50178A8817E8}',   
'Paths[SRC DimDCVentor.OLE DB Source Output]',   
'D:\demos\datafiles\DCVendorOutput.csv'  
```  
  
## <a name="remarks"></a>解説  
 データ タップを追加する、実行のインスタンスが作成の状態である必要があります (1 の値、**ステータス**の列、 [catalog.operations & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)ビュー)。 実行を処理すると状態の値が変わります。 呼び出して実行を作成することができます[catalog.create_execution & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 add_data_tap_by_guid ストアド プロシージャに関する考慮事項を以下に示します。  
  
-   データ タップを追加するとき、パッケージの実行前には検証は行われません。  
  
-   サイズが大きいデータ ファイルが生成されないように、データ タップ中にキャプチャされる行数を制限することをお勧めします。 ストアド プロシージャが実行されるコンピューターで、データ ファイル用のストレージ領域が不足した場合、ストアド プロシージャは実行を停止します。  
  
-   add_data_tap_by_guid ストアド プロシージャの実行は、パッケージのパフォーマンスに影響を与えます。 ストアド プロシージャは、データの問題のトラブルシューティングを行うことだけを目的に実行することをお勧めします。  
  
-   タップされたデータを格納するファイルにアクセスするには、ストアド プロシージャが実行されているコンピューターの管理者権限が必要です。  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーに MODIFY 権限がない。  
  
-   指定されたパッケージにおいて、指定されたコンポーネントのデータ タップが既に追加済みである。  
  
-   キャプチャする行数に指定した値が無効である。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>参照  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
  
  

