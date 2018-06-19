---
title: catalog.environment_variables (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5578c159f20a0ccbc2fca2811921270d61990da
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406084"
---
# <a name="catalogenvironmentvariables-ssisdb-database"></a>catalog.environment_variables (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての環境に対する環境変数の詳細を表示します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|環境変数の一意識別子 (ID)。|  
|environment_id|**bigint**|変数が関連付けられている環境の一意の ID。|  
|NAME|**sysname**|環境変数の名前。|  
|description|**nvarchar(1024)**|環境変数の説明。|  
|型|**nvarchar(128)**|環境変数のデータ型。|  
|sensitive|**bit**|値が `1` のとき、変数はセンシティブで、格納されるときに暗号化されます。 値が `0` のとき、変数はセンシティブではなく、値はプレーンテキストで格納されます。|  
|value|**sql_variant**|環境変数の値。 sensitive が `0` の場合、プレーンテキストの値が表示されます。 sensitive が `1` の場合、**NULL** 値が表示されます。|  
  
## <a name="remarks"></a>Remarks  
 このビューは、カタログの各環境変数の行を表示します。  
  
## <a name="permissions"></a>アクセス許可  
 このビューには、次の権限のいずれかが必要です。  
  
-   対応する環境に対する READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
