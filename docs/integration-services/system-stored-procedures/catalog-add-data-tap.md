---
title: "catalog.add_data_tap |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a25ebcc7-535e-4619-adf6-4e2b5a62ba37
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 686b40e7e1ad7f7843bee5af3295fdf394538f63
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatap"></a>catalog.add_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  パッケージ データ フロー内のコンポーネントの出力で、実行のインスタンスのデータ タップを追加します。  
  
## <a name="syntax"></a>構文  
  
```sql  
add_data_tap [ @execution_id = ] execution_id  
[ @task_package_path = ] task_package_path  
[ @dataflow_path_id_string = ] dataflow_path_id_string  
[ @data_filename = ] data_filename  
[ @max_rows = ] max_rows  
[ @data_tap_id = ] data_tap_id  
OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id =] *execution_id*  
 パッケージを含む実行の実行 ID。 *Execution_id*は、 **bigint**です。  
  
 [ @task_package_path =] *task_package_path*  
 データ フロー タスクのパッケージ パス。 **PackagePath**データ フロー タスクのプロパティ パスを指定します。 パスの大文字と小文字は区別されます。 内で、パッケージのパスを検索する[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]、データ フロー タスクを右クリックし、をクリックして**プロパティ**です。 **PackagePath**プロパティに表示されて、**プロパティ**ウィンドウです。  
  
 *Task_package_path*は、 **nvarchar (max)**です。  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 データ フロー パスの識別文字列。 パスは、2 つのデータ フロー コンポーネントを連結します。 **IdentificationString**パスのプロパティの文字列を指定します。  
  
 内で識別文字列を検索する[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]クリックして 2 つのデータ フロー コンポーネント間のパスを右クリックして**プロパティ**です。 **IdentificationString**プロパティに表示されて、**プロパティ**ウィンドウです。  
  
 *Dataflow_path_id_string*は、 **nvarchar (4000)**です。  
  
 [ @data_filename =] *data_filename*  
 タップされたデータを格納するファイルの名前。 データ フロー タスクが Foreach Loop コンテナーまたは For Loop コンテナーの中で実行される場合、ループの反復ごとにタップされたデータが個別のファイルに格納されます。 各ファイルの先頭には、反復に対応する番号が付けられます。  
  
 既定では、ファイルが格納されている、 \<*ドライブ*>: SQL server \Program Files\Microsoft フォルダーです。  
  
 *Data_filename*は、 **nvarchar (4000)**です。  
  
 [ @max_rows =] *max_rows*  
 データ タップ中にキャプチャされる行の数。 この値が指定されていない場合は、すべての行がキャプチャされます。 *Max_rows*は、 **int**です。  
  
 [ @data_tap_id =] *data_tap_id*  
 データ タップの ID を返します。 *Data_tap_id*は、 **bigint**です。  
  
## <a name="example"></a>例  
 次の例では、データ タップがデータ フロー パスで作成された`'Paths[OLE DB Source.OLE DB Source Output]`で、データ フロー タスク、`\Package\Data Flow Task`です。 タップされたデータが格納されている、`output0.txt`ファイル DataDumps フォルダー (\<*ドライブ*>: SQL server \Program Files\Microsoft)。  
  
```  
Declare @execution_id bigint  
Exec SSISDB.Catalog.create_execution @folder_name='Packages',@project_name='SSISPackages', @package_name='Package.dtsx',@reference_id=Null, @use32bitruntime=False, @execution_id=@execution_id OUTPUT  
  
Exec SSISDB.Catalog.set_execution_parameter_value @execution_id,50, 'LOGGING_LEVEL', 0  
  
Exec SSISDB.Catalog.add_data_tap @execution_id, @task_package_path='\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[OLE DB Source.OLE DB Source Output]', @data_filename = 'output0.txt'  
  
Exec SSISDB.Catalog.start_execution @execution_id  
  
```  
  
## <a name="remarks"></a>解説  
 データ タップを追加する、実行のインスタンスが作成の状態である必要があります (1 の値、**ステータス**の列、 [catalog.operations & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)ビュー)。 実行を処理すると状態の値が変わります。 呼び出して実行を作成することができます[catalog.create_execution & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 add_data_tap ストアド プロシージャに関する考慮事項を以下に示します。  
  
-   実行に親パッケージと 1 つまたは複数の子パッケージが含まれる場合、データをタップする対象パッケージごとにデータ タップを追加する必要があります。  
  
-   パッケージに同じ名前の複数のデータ フロー タスクが含まれる場合、task_package_path によって、タップされるコンポーネントの出力を含むデータ フロー タスクが一意に識別されます。  
  
-   データ タップを追加すると、パッケージの実行前に検証されません。  
  
-   サイズが大きいデータ ファイルが生成されないように、データ タップ中にキャプチャされる行数を制限することをお勧めします。 ストアド プロシージャが実行されるコンピューターで、データ ファイル用のストレージ領域が不足した場合、パッケージは実行を停止し、エラー メッセージがログに書き込まれます。  
  
-   add_data_tap ストアド プロシージャの実行は、パッケージのパフォーマンスに影響を与えます。 ストアド プロシージャは、データの問題のトラブルシューティングを行うことだけを目的に実行することをお勧めします。  
  
-   タップされたデータを格納するファイルにアクセスするには、ストアド プロシージャが実行されているコンピューターの管理者である必要があります。 また、データ タップされたパッケージを含む実行を開始したユーザーであることも必要です。  
  
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
  
## <a name="external-resources"></a>外部リソース  
 ブログ エントリ「 [SSIS 2012: データ タップのピーク](http://go.microsoft.com/fwlink/?LinkId=239983)、rafael-salas.com のです。  
  
## <a name="see-also"></a>参照  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
