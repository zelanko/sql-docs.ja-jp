---
title: "DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_SERVICE_PARAMETERS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c84d263a312318be40c65c37a168bf11fdc97cfc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingserviceparameters-rowset"></a>DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット
  サーバー上のアルゴリズムのパラメーターについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_SERVICE_PARAMETERS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|アルゴリズムの名前。|  
|**PARAMETER_NAME**|**DBTYPE_WSTR**|パラメーターの名前。|  
|**PARAMETER_TYPE**|**DBTYPE_WSTR**|パラメーターの型。|  
|**IS_REQUIRED**|**DBTYPE_BOOL**|返すブール値**TRUE**パラメーターが必要な場合です。|  
|**PARAMETER_FLAGS**|**DBTYPE_UI4**|パラメーターの特性を記述するビットマスク。<br /><br /> **DM_PARAMETER_TRAINING** (**0x0000001**)、パラメーターがトレーニングに使用されることを示します。<br /><br /> **DM_PARAMETER_PREDICTION** (**0x00000002**)、パラメーターが予測に使用されることを示します。<br /><br /> **DM_PARAMETER_CONTENT** (**0x00000003**)、パラメーターがコンテンツの制限に使用されることを示します。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|パラメーターについてのわかりやすい説明。|  
|**DEFAULT_VALUE です。**|**DBTYPE_WSTR**|パラメーターの既定値です。 返します**NULL**既定値は、単純なデータ型ではない場合。|  
|**VALUE_ENUMERATION**|**DBTYPE_WSTR**|使用可能なパラメーター値の列挙子。|  
|**HELP_FILE**|**DBTYPE_WSTR**|このパラメーターのマニュアルを含んでいるファイルの名前。|  
|**HELP_CONTEXT**|**DBTYPE_I4**|この関数のヘルプ コンテキスト ID。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_SERVICE_PARAMETERS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**PARAMETER_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
