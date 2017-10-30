---
title: "catalog.event_message_context |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7aeb07c52f7ed00aa5a6a29cdd054258cb62d65
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーでの実行について、実行イベントのメッセージに関連付けられた条件に関する情報を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Context_id|bigint|エラー コンテキストの一意の ID。|  
|Event_message_id|bigint|コンテキストに関連するメッセージの一意の ID。|  
|Context_depth|int|深さが増えるにつれて、コンテキストはエラーからかけ離れたものになります。 エラーが発生した場合、コンテキストの深さは 1 から始まります。 値 0 は、実行が開始される前のパッケージの状態を示します。|  
|Package_path|nvarchar (max)|コンテキスト ソースのパッケージ パス。|  
|Context_type|smallint|コンテキストのソースであるオブジェクトの型。 参照してください、**解説**コンテキストの種類の一覧のセクションでします。|  
|Context_source_name|Nvarchar (4000)|コンテキストのソースであるオブジェクトの名前。|  
|Context_source_id|Nvarchar(38)|コンテキストのソースであるオブジェクトの一意の ID。|  
|Property_name|Nvarchar (4000)|コンテキストのソースに関連付けられているプロパティの名前。|  
|Property_value|sql_variant 型|コンテキストのソースに関連付けられているプロパティ値。|  
  
## <a name="remarks"></a>解説  
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
|80|[ODBC 入力先エディター]|接続マネージャーのプロパティ。|  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール。  
  
-   メンバーシップを**sysadmin**サーバーの役割です。  
  
  

