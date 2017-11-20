---
title: "catalog.validations (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
ms.assetid: dbafe110-b480-48f3-b45f-31d71ca68f62
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2d799fd23c2adef75e3dcf4543e9e0ee6271c9b5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidations-ssisdb-database"></a>catalog.validations (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  内のすべてのプロジェクトおよびパッケージ検証の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|validation_id|**bigint**|検証の一意識別子 (ID)。|  
|environment_scope|**Char (1)**|検証が考慮する環境参照を示します。 値が `A` の場合は、プロジェクトに関連するすべての環境参照が検証に含まれます。 値が `S` の場合は、1 つの環境参照のみが含まれます。 値が`D`、環境参照は含まれず、各パラメーターでは、検証に合格するために既定のリテラル値があります。|  
|validate_type|**Char (1)**|実行する検証の種類。 依存関係の検証の検証のタイプがあります (`D`) または完全検証 (`F`)。 パッケージの検証では、常に完全検証が実施されます。|  
|folder_name|**nvarchar (128)**|対応するプロジェクトを含むフォルダーの名前。|  
|project_name|**nvarchar (128)**|プロジェクトの名前。|  
|project_lsn|**bigint**|検証されるプロジェクトのバージョン。|  
|use32bitruntime|**bit**|64 ビット オペレーティング システムで 32 ビットのランタイムを使用してパッケージを実行するかどうかを示します。 値が`1`、32 ビット ランタイムで実行します。 値が`0`、64 ビット ランタイムで実行します。|  
|reference_id|**bigint**|環境を参照するためプロジェクトによって使用されるプロジェクト環境参照の ID。|  
|operation_type|**smallint**|操作の種類。 このビューに表示される操作は、プロジェクトの検証を含める (`300`) とパッケージ検証 (`301`)。|  
|object_name|**nvarhcar(260)**|オブジェクトの名前。|  
|object_type|**smallint**|オブジェクトの種類。 オブジェクトは、プロジェクトである可能性があります (`20`) またはパッケージ (`30`)。|  
|object_id|**bigint**|操作の影響を受けるオブジェクトの ID。|  
|start_time|**datetimeoffset (7)**|操作が開始された時刻。|  
|end_time|**datetimeoffsset(7)**|操作が終了時刻。|  
|ステータス|**int**|操作の状態。 使用可能な値が作成されます (`1`)、実行中 (`2`)、取り消し済み (`3`) に失敗しました (`4`)、保留中 (`5`)、予期しない終了 (`6`)、成功 (`7`)、(を停止しています`8`)、および完了した (`9`)。|  
|caller_sid|**varbinary (85)**|ログオンに Windows 認証が使用された場合はユーザーのセキュリティ ID (SID)。|  
|させていただきたいと|**nvarchar (128)**|操作を実行したアカウントの名前。|  
|process_id|**int**|外部プロセスのプロセス ID (該当する場合)。|  
|stopped_by_sid|**varbinary (85)**|操作を停止したユーザーの SID。|  
|stopped_by_name|**nvarchar (128)**|操作を停止したユーザーの名前。|  
|server_name|**nvarchar (128)**|指定のインスタンスの Windows サーバーとインスタンス情報[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|machine_name|**nvarchar (128)**|サーバー インスタンスが稼働しているコンピューターの名前。|  
|dump_id|**uniqueidentifier**|実行ダンプの ID。|  
  
## <a name="remarks"></a>解説  
 このビューの各検証に対して 1 つの行を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   対応する操作に対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

