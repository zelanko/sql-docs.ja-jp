---
title: "catalog.environment_variables (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 40e31b9697c453f6a9d60dfcc8d9302dfefe0ac4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべての環境に対する環境変数の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|環境変数の一意識別子 (ID)。|  
|environment_id|**bigint**|変数が関連付けられている環境の一意の ID。|  
|name|**sysname**|環境変数の名前。|  
|description|**nvarchar (1024)**|環境変数の説明。|  
|型|**nvarchar (128)**|環境変数のデータ型。|  
|sensitive|**bit**|値が`1`変数が機密性の高い、格納されるときに暗号化されます。 値が `0` のとき、変数はセンシティブではなく、値はプレーンテキストで格納されます。|  
|value|**sql_variant**|環境変数の値。 機密性の高いときに`0`、プレーン テキスト値が表示されます。 機密性の高いときは`1`、 **NULL**値が表示されます。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの各環境変数の行を表示します。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   対応する環境に対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
