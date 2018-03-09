---
title: "DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_MODEL_CONTENT_PMML
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 771ce7da7719b186dffef3ae0f3095a215c71e48
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]マイニング モデルの XML 構造を返します。 XML 文字列の形式は、Predictive Model Markup Language (PMML 2.1) 規格に従います。  
  
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
|**サイズ**|**DBTYPE_UI4**||XML 文字列のバイト数。|  
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
  
  
