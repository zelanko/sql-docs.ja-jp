---
title: "catalog.set_execution_parameter_value (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 055d86c9-befd-4e63-acb1-6dfe833549d2
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 7b13e7b1c28bad6e573e829183372da4bb62f92d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="catalogsetexecutionparametervalue-ssisdb-database"></a>catalog.set_execution_parameter_value (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行のインスタンスにパラメーターの値を設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 実行インスタンス開始後は、パラメーターの値は変更できません。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.set_execution_parameter_value [ @execution_id = execution_id  
    , [ @object_type = ] object_type  
    , [ @parameter_name = ] parameter_name  
    , [ @parameter_value = ] parameter_value  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id =] *execution_id*  
 実行のインスタンスの一意の識別子。 *Execution_id*は**bigint**です。  
  
 [ @object_type =] *object_type*  
 パラメーターの型。  
  
 次のパラメーター設定*object_type*に 50  
  
-   LOGGING_LEVEL  
  
-   CUSTOMIZED_LOGGING_LEVEL  
  
-   DUMP_ON_ERROR  
  
-   DUMP_ON_EVENT  
  
-   DUMP_EVENT_CODE  
  
-   CALLER_INFO  
  
-   SYNCHRONIZED  
  
 値を使用して`20`プロジェクト パラメーターまたは値を示す`30`パッケージ パラメーターを示すためにします。  
  
 *Object_type*は**smallint**です。  
  
 [ @parameter_name =] *parameter_name*  
 パラメーターの名前。 *Parameter_name*は**nvarchar (128)**です。  
  
 [ @parameter_value =]*パラメーター*  
 パラメーターの値。 *パラメーター*は**sql_variant**です。  
  
## <a name="remarks"></a>解説  
 特定の実行に使用されたパラメーター値を調べるには、catalog.execution_parameter_values ビューに対してクエリを実行します。  
  
 パッケージの実行中にログに記録される情報のスコープを指定するには、次のように設定します。 *parameter_name*を LOGGING_LEVEL に設定し*パラメーター*値は次のいずれかにします。  
  
 設定、 *object_type*パラメーターを 50 にします。  
  
|[値]|説明|  
|-----------|-----------------|  
|0|なし<br /><br /> ログ記録をオフにします。 パッケージの実行状態のみがログに記録されます。|  
|1|Basic<br /><br /> カスタム イベントと診断イベントを除く、すべてのイベントをログに記録します。 これが既定値です。|  
|2|パフォーマンス<br /><br /> パフォーマンス統計、および OnError イベントと OnWarning のイベントのみをログに記録します。|  
|3|Verbose<br /><br /> カスタム イベントと診断イベントを含む、すべてのイベントをログに記録されます。 <br />カスタム イベントには、Integration Services タスクによってログに記録されるイベントを含みます。 詳細については、次を参照してください[Custom Messages for Logging。](../../integration-services/performance/integration-services-ssis-logging.md#custom_messages)|  
|4|ランタイムの系列<br /><br /> データ フロー内の系列を追跡するために必要なデータを収集します。|  
|100|カスタムのログ記録レベル<br /><br /> CUSTOMIZED_LOGGING_LEVEL パラメーターの設定を指定します。 指定できる値についての詳細については、次を参照してください。 [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md)です。<br /><br /> カスタマイズされたログ記録レベルの詳細については、次を参照してください。 [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)です。|  
  
 パッケージの実行中にエラーが発生した場合に、Integration Services サーバーによりダンプ ファイルが生成されるように指定するには、未実行の実行インスタンスに次のパラメーター値を設定します。  
  
|パラメーター|[値]|  
|---------------|-----------|  
|*execution_id*|実行のインスタンスの一意識別子|  
|*object_type*|50|  
|*parameter_name*|‘DUMP_ON_ERROR|  
|*パラメーター*|1|  
  
 パッケージの実行中にイベントが発生した場合に、Integration Services サーバーによりダンプ ファイルを生成されるように指定するには、未実行の実行インスタンスに次のパラメーター値を設定します。  
  
|パラメーター|[値]|  
|---------------|-----------|  
|*execution_id*|実行のインスタンスの一意識別子|  
|*object_type*|50|  
|*parameter_name*|‘DUMP_ON_EVENT|  
|*パラメーター*|1|  
  
 パッケージの実行中に、Integration Services サーバーによるダンプ ファイルの生成が行われる原因となるイベントを指定するには、未実行の実行インスタンスに次のパラメーター値を設定します。 複数のイベント コードは、セミコロンで区切ります。  
  
|パラメーター|[値]|  
|---------------|-----------|  
|*execution_id*|実行のインスタンスの一意識別子|  
|*object_type*|50|  
|*parameter_name*|DUMP_EVENT_CODE|  
|*パラメーター*|1 つまたは複数のイベント コード|  
  
## <a name="example"></a>例  
 次の例では、パッケージの実行中にエラーが発生した場合に、Integration Services サーバーによりダンプ ファイルが生成されるように指定しています。  
  
```sql
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_ERROR',1  
```  
  
## <a name="example"></a>例  
 次の例では、パッケージの実行中にイベントが発生した場合に、Integration Services サーバーによりダンプ ファイルが生成されるように指定し、サーバーによるファイルの生成が行われる原因となるイベントを指定しています。  
  
```sql
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_EVENT',1  
  
declare @event_code nvarchar(50)  
set @event_code = '0xC020801C'  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_EVENT_CODE', @event_code  
```  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ および MODIFY 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 エラーまたは警告が発生する可能性がある条件を以下に示します。  
  
-   ユーザーに適切な権限がない  
  
-   実行識別子が有効ではない  
  
-   パラメーター名が無効  
  
-   パラメーター値のデータ型が、パラメーターのデータ型と一致しない  
  
## <a name="see-also"></a>参照  
 [catalog.execution_parameter_values & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)   
 [パッケージ実行用のダンプ ファイルを生成する](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
