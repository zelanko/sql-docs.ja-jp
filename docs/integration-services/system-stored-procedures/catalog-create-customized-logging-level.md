---
title: "catalog.create_customized_logging_level |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: 20b3ba0a-126f-49bf-b70f-61b2a0fcb750
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 126fa0af811033bb0be035b1f4c550620c696bb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreatecustomizedlogginglevel"></a>catalog.create_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  新しいカスタマイズされたログ記録レベルを作成します。 カスタマイズされたログ記録レベルの詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_customized_logging_level [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
    , [ @profile_value = ] profile_value  
    , [ @event_value = ] event_value  
    , [ @level_id = ] level_id OUT   
```  
  
## <a name="arguments"></a>引数  
 [ @level_name =] *level_name*  
 新しいの既存の名前は、ログ記録レベルをカスタマイズします。  
  
 *Level_name*は**nvarchar (128)**です。  
  
 [ @level_description =] *level_description*  
 新しいの既存の説明では、ログ記録レベルをカスタマイズします。  
  
 *Level_description*は**nvarchar (1024)**です。  
  
 [ @profile_value =] *profile_value*  
 新しいする統計情報は、ログに記録するログ記録レベルをカスタマイズできます。  
  
 統計情報の有効な値には、次の項目が含まれます。 値をこれらの値に対応しており、**統計**のタブ、**ログ記録レベルのカスタマイズ管理** ダイアログ ボックス。  
  
-   実行 = 0  
  
-   ボリューム = 1  
  
-   パフォーマンス = 2  
  
 *Profile_value*は、 **bigint**です。  
  
 [ @event_value =] *event_value*  
 新しいイベントは、ログに記録するログ記録レベルをカスタマイズできます。  
  
 イベントの有効な値には、次の項目が含まれます。 値をこれらの値に対応しており、**イベント**のタブ、**ログ記録レベルのカスタマイズ管理** ダイアログ ボックス。  
  
|イベントをイベントのコンテキスト|イベントのコンテキストを持つイベント|  
|----------------------------------|-------------------------------|  
|OnVariableValueChanged = 0<br /><br /> OnExecutionStatusChanged = 1<br /><br /> OnPreExecute = 2<br /><br /> OnPostExecute = 3<br /><br /> OnPreValidate = 4<br /><br /> OnPostValidate = 5<br /><br /> OnWarning = 6<br /><br /> OnInformation = 7<br /><br /> OnError = 8<br /><br /> OnTaskFailed = 9<br /><br /> OnProgress = 10<br /><br /> OnQueryCancel = 11<br /><br /> OnBreakpointHit = 12<br /><br /> OnCustomEvent = 13<br /><br /> 診断 = 14<br /><br /> DiagnosticEx = 15<br /><br /> NonDiagnostic = 16|OnVariableValueChanged_IncludeContext = 32<br /><br /> OnExecutionStatusChanged_IncludeContext = 33<br /><br /> OnPreExecute_IncludeContext = 34<br /><br /> OnPostExecute_IncludeContext 35 を =<br /><br /> OnPreValidate_IncludeContext 36 を =<br /><br /> OnPostValidate_IncludeContext 37 を =<br /><br /> OnWarning_IncludeContext = 38<br /><br /> OnInformation_IncludeContext = 39<br /><br /> OnError_IncludeContext = 40<br /><br /> OnTaskFailed_IncludeContext = 41<br /><br /> OnProgress_IncludeContext 42 を =<br /><br /> OnQueryCancel_IncludeContext 43 を =<br /><br /> OnBreakpointHit_IncludeContext = 44<br /><br /> OnCustomEvent_IncludeContext = 45<br /><br /> Diagnostic_IncludeContext 46 を =<br /><br /> DiagnosticEx_IncludeContext = 47<br /><br /> NonDiagnostic_IncludeContext 48 を =|  
  
 *Event_value*は、 **bigint**です。  
  
 [ @level_id =] *level_id*アウト  
 新しい id では、ログ記録レベルをカスタマイズします。  
  
 *Level_id*は、 **bigint**です。  
  
## <a name="remarks"></a>解説  
 TRANSACT-SQL での複数の値を結合する、 *profile_value*または*event_value*引数では、この例に従って操作します。 OnError (8) と DiagnosticEx (15) イベントを計算する式をキャプチャする*event_value*は`2^8 + 2^15 = 33024`します。  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーには、必要なアクセス許可がありません。  
  
  

