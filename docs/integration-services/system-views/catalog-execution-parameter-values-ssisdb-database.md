---
title: "catalog.execution_parameter_values (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 60907a82f3d0bb9f273355fd6bfbd7378ce72c9f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  インスタンスの実行中に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージによって使用される実際のパラメーター値を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|実行パラメーターの一意識別子 (ID)。|  
|execution_id|**bigint**|実行のインスタンスの一意の ID。|  
|object_type|**smallint**|値が`20`パラメーターはプロジェクト パラメーターです。 値が `30` の場合、パラメーターはパッケージ パラメーターです。 値が`50`パラメーターは、次のいずれか。<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **同期されています。**|  
|parameter_data_type|**nvarchar (128)**|パラメーターのデータ型です。|  
|parameter_name|**sysname**|パラメーターの名前。|  
|parameter_value|**sql_variant**|パラメーターの値。 機密性の高いときに`0`、プレーン テキスト値が表示されます。 機密性の高いときは`1`、 **NULL**値が表示されます。|  
|sensitive|**bit**|値が`1`パラメーター値はセンシティブです。 値が `0` の場合、パラメーター値はセンシティブではありません。|  
|required|**bit**|値が `1` の場合、実行を開始するためパラメーター値が必要です。 値が `0` の場合、実行を開始するためのパラメーター値は不要です。|  
|value_set|**bit**|値が`1`パラメーター値が割り当てられています。 値が`0`パラメーターの値が割り当てられていません。|  
|runtime_override|**bit**|値が`1`パラメーターの値は、実行が開始する前に、元の値から変更されました。 値が `0` の場合、パラメーター値は割り設定された元の値です。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの実行の各パラメーターの行を表示します。 実行パラメーター値は、1 つのインスタンスの実行中にプロジェクト パラメーターまたはパッケージ パラメーターに割り当てられた値です。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

