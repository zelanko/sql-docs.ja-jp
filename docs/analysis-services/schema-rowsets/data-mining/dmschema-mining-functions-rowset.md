---
title: DMSCHEMA_MINING_FUNCTIONS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f92a3028f9397283f8d5820c54d823e40b8fdc3d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  実行しているサーバーで使用できるデータ マイニング アルゴリズムでサポートされているデータ マイニング関数について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_FUNCTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**||アルゴリズムの名前。|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**||関数の名前です。|  
|**FUNCTION_SIGNATURE**|**DBTYPE_WSTR**||関数の署名。|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||**FALSE**関数がスカラー コンテンツ (など、文字の引数の長さ); を返す場合**TRUE**場合は、ヒストグラム テーブルなどのテーブルを返します。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||関数についてのわかりやすい説明。|  
|**HELP_FILE**|**DBTYPE_WSTR**||この関数のマニュアルを含んでいるファイルの名前。|  
|**HELP_CONTEXT**|**DBTYPE_I4**||この関数のヘルプ コンテキスト ID。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_FUNCTIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**FUNCTION_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
