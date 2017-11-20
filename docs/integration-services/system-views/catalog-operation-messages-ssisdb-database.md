---
title: "catalog.operation_messages (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- catalog.operation_messages view [Integration Services]
- operation_messages view [Integration Services]
ms.assetid: 0b3cbe38-ce24-47ca-83ef-6538a5299d1a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 235e9896cbf075bdc26e3df120b23091b8e82d6d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogoperationmessages-ssisdb-database"></a>catalog.operation_messages (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  操作中にログに記録されるメッセージが表示されます、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|operation_message_id|**bigint**|メッセージの一意識別子 (ID)。|  
|operation_id|**bigint**|操作の一意の ID。|  
|message_time|**datetimeoffset (7)**|メッセージが作成された時間。|  
|message_type|**smallint**|表示されるメッセージの種類。|  
|message_source_type|**smallint**|メッセージ ソースの種類の ID。|  
|message|**nvarchar(max)**|メッセージのテキストです。|  
|extended_info_id|**bigint**|操作メッセージに関連する追加の情報の ID で見つかった、 [extended_operation_info](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)ビュー。|  
  
## <a name="remarks"></a>解説  
 このビューには、カタログでの操作中に記録される各メッセージの行が表示されます。 このメッセージは、サーバー、パッケージの実行プロセス、または実行エンジンによって生成されます。  
  
 このビューに表示されるメッセージの種類は次のとおりです。  
  
|**message_type**値|Description|  
|-----------------------------|-----------------|  
|-1|Unknown|  
|120|[エラー]|  
|110|警告|  
|70|情報|  
|10|検証済み|  
|20|検証後|  
|30|事前に実行します。|  
|40|実行後|  
|60|進行状況|  
|50|StatusChange|  
|100|QueryCancel|  
|130|TaskFailed|  
|90|Diagnostic|  
|200|Custom|  
|140|DiagnosticEx<br /><br /> パッケージ実行タスクでは、子パッケージを実行するたびに、このイベントを記録します。 イベント メッセージは、子パッケージに渡されたパラメーター値で構成されます。<br /><br /> DiagnosticEx のメッセージ列の値は XML テキストです。|  
|400|NonDiagnostic|  
|80|VariableValueChanged|  
  
 このビューに表示されるメッセージ ソースの種類は次のとおりです。  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|T-SQL や CLR ストアド プロシージャのようなエントリの API|  
|20|パッケージ (ISServerExec.exe) を実行するために使用する外部プロセス|  
|30|パッケージ レベルのオブジェクト|  
|40|制御フロー タスク|  
|50|制御フロー コンテナー|  
|60|データ フロー タスク|  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

