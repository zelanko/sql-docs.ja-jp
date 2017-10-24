---
title: "DMSCHEMA_MINING_MODEL_XML 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODEL_XML
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0d508a1bc916d75ff33e5aba19c6306a547af8fb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingmodelxml-rowset"></a>DMSCHEMA_MINING_MODEL_XML 行セット
  マイニング モデルの XML 構造を返します。 XML 文字列の形式は、Predictive Model Markup Language (PMML 2.1) 規格に従います。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_MODEL_XML**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||カタログ名。 モデルがメンバーとして含まれているデータベースの名前を使用して設定されます。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||修飾されていないスキーマ名。 は、この列はサポートされていない[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**MODEL_NAME**|**DBTYPE_WSTR**||モデル名。 この列を含めることはできません**NULL**です。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||モデルの種類。 プロバイダー固有の文字列であり、 できます**NULL**です。|  
|**MODEL_GUID**|**DBTYPE_GUID 型**||モデルを識別する GUID。 テーブルの識別に Guid を使用しないプロバイダーを返す**NULL**です。|  
|**MODEL_PMML**|**DBTYPE_WSTR**||PMML 形式でのモデルのコンテンツの XML 表現。|  
|**サイズ**|**DBTYPE_UI4**||XML 文字列のバイト数。|  
|**場所**|**DBTYPE_WSTR**||XML ファイルの場所。 **NULL**記憶域の物理ファイルを使用しない場合。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 DMSCHEMA_MINING_MODEL_XML 行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_W**STR|省略可。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

