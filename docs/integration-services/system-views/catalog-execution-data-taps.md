---
title: catalog.execution_data_taps | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 582c0554d7ffab10ee65bf74ecdb50e72169dd24
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="catalogexecutiondatataps"></a>catalog.execution_data_taps
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行で定義されたデータ タップごとに情報が表示されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|データ タップの一意識別子 (ID)。|  
|execution_id|**bigint**|実行のインスタンスの一意識別子 (ID)。|  
|package_path|**nvarchar(max)**|データがタップされたデータ フロー タスクのパッケージ パス。|  
|dataflow_path_id_string|**nvarchar (4000)**|データ フロー パスの識別文字列です。|  
|dataflow_task_guid|**uniqueidentifier**|データ フロー タスクの一意 の ID。|  
|max_rows|**int**|キャプチャする行の数。 この値が指定されていない場合は、すべての行がキャプチャされます。|  
|filename|**nvarchar (4000)**|データ ダンプ ファイルの名前。 詳細については、「 [パッケージ実行用のダンプ ファイルを生成する](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
## <a name="see-also"></a>参照  
 [パッケージ実行用のダンプ ファイルを生成する](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
