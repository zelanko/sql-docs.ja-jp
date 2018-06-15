---
title: DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd478b0185feffad77848f5c727c81931d57f9f5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028022"
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  マイニング モデルの XML 構造を返します。 XML 文字列の形式は、Predictive Model Markup Language (PMML 2.1) 規格に従います。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_MODEL_CONTENT_PMML**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||モデルがメンバーとして含まれているデータベースの名前を使用して設定されるカタログ名。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||修飾されていないスキーマ名。 は、この列はサポートされていない[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**MODEL_NAME**|**DBTYPE_WSTR**||モデル名。 この列を含めることはできません**NULL**です。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||モデルの種類。 プロバイダー固有の文字列であり、 できます**NULL**です。|  
|**MODEL_GUID**|**DBTYPE_GUID 型**||モデルを識別する GUID。 テーブルの識別に Guid を使用しないプロバイダーを返す**NULL**です。|  
|**MODEL_PMML**|**DBTYPE_WSTR**||PMML 形式でのモデルのコンテンツの XML 表現。|  
|**SIZE**|**DBTYPE_UI4**||XML 文字列のバイト数。|  
|**場所**|**DBTYPE_WSTR**||XML ファイルの場所。 **NULL**場所が使用できない場合。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_MODEL_CONTENT_PMML**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
