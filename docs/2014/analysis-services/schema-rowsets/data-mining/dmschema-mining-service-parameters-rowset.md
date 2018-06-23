---
title: DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_SERVICE_PARAMETERS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9079be52d50da3a400496dc602166c857f2b1691
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173343"
---
# <a name="dmschemaminingserviceparameters-rowset"></a>DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット
  サーバー上のアルゴリズムのパラメーターについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_SERVICE_PARAMETERS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||アルゴリズムの名前。|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`||パラメーターの名前。|  
|`PARAMETER_TYPE`|`DBTYPE_WSTR`||パラメーターの型。|  
|`IS_REQUIRED`|`DBTYPE_BOOL`||パラメーターが必須の場合に `TRUE` を返すブール値。|  
|`PARAMETER_FLAGS`|`DBTYPE_UI4`||パラメーターの特性を記述するビットマスク。<br /><br /> -   `DM_PARAMETER_TRAINING` (`0x0000001`)、パラメーターがトレーニングに使用されることを示します。<br />-   `DM_PARAMETER_PREDICTION` (`0x00000002`)、パラメーターが予測に使用されることを示します。<br />-   `DM_PARAMETER_CONTENT` (`0x00000003`)、パラメーターがコンテンツの制限に使用されることを示します。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||パラメーターについてのわかりやすい説明。|  
|`DEFAULT_VALUE`|`DBTYPE_WSTR`||パラメーターの既定値です。 既定値が単純なデータ型でない場合は `NULL` を返します。|  
|`VALUE_ENUMERATION`|`DBTYPE_WSTR`||使用可能なパラメーター値の列挙子。|  
|`HELP_FILE`|`DBTYPE_WSTR`||このパラメーターのマニュアルを含んでいるファイルの名前。|  
|`HELP_CONTEXT`|`DBTYPE_I4`||この関数のヘルプ コンテキスト ID。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_SERVICE_PARAMETERS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|任意。|  
|`PARAMETER_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  