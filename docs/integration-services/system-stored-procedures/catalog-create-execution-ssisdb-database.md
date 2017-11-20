---
title: "catalog.create_execution (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
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
ms.assetid: 45d0c2f6-1f38-445f-ac06-e2a01f6ac600
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7e9d38935a91bba81359bee7fdbd64dba86d0d26
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogcreateexecution-ssisdb-database"></a>catalog.create_execution (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行のインスタンスを作成します。  
  
 このストアド プロシージャは既定のサーバーのログ レベルを使用します。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_execution [@folder_name = folder_name  
     , [@project_name =] project_name  
     , [@package_name =] package_name  
  [  , [@reference_id =] reference_id ]  
  [  , [@use32bitruntime =] use32bitruntime ] 
  [  , [@runinscaleout =] runinscaleout ]
  [  , [@useanyworker =] useanyworker ] 
     , [@execution_id =] execution_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [@folder_name =] *folder_name*  
 実行するパッケージが格納されているフォルダーの名前。 *Folder_name*は**nvarchar (128)**です。  
  
 [@project_name =] *project_name*  
 実行するパッケージを含むプロジェクトの名前。 *Project_name*は**nvarchar (128)**です。  
  
 [@package_name =] *package_name*  
 実行するパッケージの名前。 *Package_name*は**nvarchar (260)**です。  
  
 [@reference_id =] *reference_id*  
 環境参照の一意識別子。 このパラメーターはオプションです。 *Reference_id*は**bigint**です。  
  
 [@use32bitruntime =] *use32bitruntime*  
 64 ビット オペレーティング システムでパッケージを実行する 32 ビット ランタイムを使用するかどうかを示します。 64 ビットのオペレーティング システムで実行されているときに、32 ビット ランタイムを使用してパッケージを実行するのにには、1 の値を使用します。 値 0 を使用すると、64 ビット オペレーティング システムで実行しているときに、64 ビット ランタイムでパッケージを実行します。 このパラメーターはオプションです。 *Use32bitruntime*は**ビット**です。  
 
 [@runinscaleout =] *runinscaleout*  
 実行がスケール アウトであるかどうかを示します。1 の値を使用してスケール アウトでパッケージを実行します。スケール アウトせずパッケージを実行するのにには、0 の値を使用します。このパラメーターはオプションです。 指定しない場合、その値は [ssisdb] DEFAULT_EXECUTION_MODE に設定されます。[カタログ] です。[catalog_properties] です。 *Runinscaleout*は**ビット**です。 
 
 [@useanyworker =] *useanyworker*  
  実行を行うには、スケール アウト ワーカーを許可するかどうかを示します。 スケール アウト ワーカーを使用してパッケージを実行するのにには、1 の値を使用します。 パッケージを実行するのにすべてのスケール アウト ワーカーが許可されていることを示すために 0 の値を使用します。 このパラメーターはオプションです。 指定しない場合、その値は 1 に設定します。 *Useanyworker*は**ビット**です。 
  
 [@execution_id =] *execution_id*  
 実行のインスタンスの一意識別子を返します。 *Execution_id*は**bigint**です。  

  
## <a name="remarks"></a>解説  
 実行は、パッケージの実行の 1 つのインスタンス中にパッケージによって使用されるパラメーター値を指定するために使用されます。  
  
 環境参照が指定した場合、 *reference_id*パラメーター、ストアド プロシージャは、プロジェクト パラメーターおよびパッケージ パラメーターをリテラル値や対応する環境変数から参照されている値を設定します。 環境参照が指定されている場合は、パッケージの実行中、既定のパラメーター値が使用されます。 実行の特定のインスタンスに使用される値を正確に確認するには*execution_id*出力から、このストアド プロシージャとクエリ パラメーターの値を[execution_parameter_values](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)ビュー。  
  
 実行で指定できるのは、エントリ ポイントのパッケージとしてマークされたパッケージのみです。 エントリ ポイントではないパッケージを指定すると、実行が失敗します。  
  
## <a name="example"></a>例  
 次の例では、スケール アウトではない Child1.dtsx パッケージの実行のインスタンスを作成する catalog.create_execution を呼び出します。integration Services Project1 にはパッケージが含まれています。 例では catalog.set_execution_parameter_value を呼び出して、Parameter1、Parameter2、および LOGGING_LEVEL の各パラメーターの値を設定します。 例では catalog.start_execution を呼び出して、実行のインスタンスを起動します。  
  
```sql  
Declare @execution_id bigint  
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Child1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'TestDeply4', @project_name=N'Integration Services Project1', @use32bitruntime=False, @reference_id=Null  
Select @execution_id  
DECLARE @var0 sql_variant = N'Child1.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter1', @parameter_value=@var0  
DECLARE @var1 sql_variant = N'Child2.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter2', @parameter_value=@var1  
DECLARE @var2 smallint = 1  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var2  
EXEC [SSISDB].[catalog].[start_execution] @execution_id  
GO  
```  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ および EXECUTE 実行権限と、該当する場合は、参照先の環境での READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  

 場合@runinscaleout1 の場合は、ストアド プロシージャでは、次の権限のいずれかが必要です。
 
-   メンバーシップを**ssis_admin**データベース ロール

-   メンバーシップを**ssis_cluster_executor**データベース ロール

-   メンバーシップを**sysadmin**サーバーの役割
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 次に、エラーまたは警告を発生させることがある条件を説明します。  
  
-   パッケージがありません。  
  
-   ユーザーには、適切なアクセス許可がありません。  
  
-   環境参照*reference_id*、無効です。  
  
-   指定したパッケージが、エントリ ポイントのパッケージではない。  
  
-   参照先の環境変数のデータ型が、プロジェクトまたはパッケージ パラメーターのデータ型と異なる。  
  
-   プロジェクトまたはパッケージに、値が必要なパラメーターが含まれているが、値が割り当てられていない。  
  
-   参照先の環境変数が、環境参照を環境に見つかりません*reference_id*を指定します。  
  
## <a name="see-also"></a>参照  
 [catalog.start_execution & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)   
 [catalog.set_execution_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [catalog.add_execution_worker & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)  
  

