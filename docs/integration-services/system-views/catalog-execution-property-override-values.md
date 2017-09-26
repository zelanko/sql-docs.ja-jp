---
title: "catalog.execution_property_override_values |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ed9ae4ea7a7165efe53a551832d8e4a0eb7a2114
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  パッケージの実行中に設定されたプロパティ オーバーライド値を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|プロパティ オーバーライド値の一意の ID。|  
|execution_id|**bigint**|実行のインスタンスの一意の ID。|  
|property_path|**nvarchar (4000)**|パッケージ内のプロパティのパス。|  
|property_value|**nvarchar(max)**|プロパティのオーバーライド値。|  
|sensitive|**bit**|値が 1 のとき、プロパティはセンシティブで、格納されるときに暗号化されます。 値が 0 のとき、プロパティはセンシティブではなく、値はプレーンテキストで格納されます。|  
  
## <a name="remarks"></a>解説  
 このビューを使用するプロパティの値がオーバーライドされた実行ごとに行を表示、**プロパティのオーバーライド**」の「、**詳細**のタブ、**パッケージ実行**ダイアログ ボックス。 プロパティへのパスがから派生した、**パッケージ パス**パッケージ タスクのプロパティです。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
