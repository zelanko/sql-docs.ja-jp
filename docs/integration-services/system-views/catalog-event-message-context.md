---
title: catalog.event_message_context | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 593931ad7aa343229cfac934cd2ce2648bdddb99
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーでの実行について、実行イベントのメッセージに関連付けられた条件に関する情報を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Context_id|BIGINT|エラー コンテキストの一意の ID。|  
|Event_message_id|BIGINT|コンテキストに関連するメッセージの一意の ID。|  
|Context_depth|ssNoversion|深さが増えるにつれて、コンテキストはエラーからかけ離れたものになります。 エラーが発生した場合、コンテキストの深さは 1 から始まります。 値 0 は、実行が開始される前のパッケージの状態を示します。|  
|Package_path|Nvarchar(max)|コンテキスト ソースのパッケージ パス。|  
|Context_type|SMALLINT|コンテキストのソースであるオブジェクトの型。 コンテキストの種類の一覧については、「**解説**」セクションを参照してください。|  
|Context_source_name|Nvarchar (4000)|コンテキストのソースであるオブジェクトの名前。|  
|Context_source_id|Nvarchar(38)|コンテキストのソースであるオブジェクトの一意の ID。|  
|Property_name|Nvarchar (4000)|コンテキストのソースに関連付けられているプロパティの名前。|  
|Property_value|Sql_variant|コンテキストのソースに関連付けられているプロパティ値。|  
  
## <a name="remarks"></a>Remarks  
 次の表に、コンテキストの種類の一覧を示します。  
  
||||  
|-|-|-|  
|コンテキストの種類の値|種類名|Description|  
|10|タスク|エラーが発生したときのタスクの状態。|  
|20|パイプライン|パイプライン コンポーネント (ソース、変換先、または変換コンポーネント) でのエラー。|  
|30|Sequence|シーケンスの状態。|  
|40|For ループ|For ループの状態。|  
|50|Foreach ループ|Foreach ループの状態。|  
|60|[パッケージ]|エラーが発生したときのパッケージの状態。|  
|70|変数|変数の値|  
|80|[ODBC 入力元エディター]|接続マネージャーのプロパティ。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ。  
  
-   **sysadmin** サーバー ロールのメンバーシップ。  
  
  
