---
title: DMSCHEMA_MINING_MODEL_XML 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODEL_XML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3be57336379c66577c245a891e047ec95f763fd9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130822"
---
# <a name="dmschemaminingmodelxml-rowset"></a>DMSCHEMA_MINING_MODEL_XML 行セット
  マイニング モデルの XML 構造を返します。 XML 文字列の形式は、Predictive Model Markup Language (PMML 2.1) 規格に従います。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_MODEL_XML`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||カタログ名。 モデルがメンバーとして含まれているデータベースの名前を使用して設定されます。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||修飾されていないスキーマ名。 この列は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でサポートされていないため、常に `NULL` が格納されます。|  
|`MODEL_NAME`|`DBTYPE_WSTR`||モデル名。 この列に `NULL` を含めることはできません。|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||モデルの種類。 プロバイダー固有の文字列であり、 `NULL` になる場合があります。|  
|`MODEL_GUID`|`DBTYPE_GUID`||モデルを識別する GUID。 テーブルの識別に GUID を使用しないプロバイダーは、`NULL` を返します。|  
|`MODEL_PMML`|`DBTYPE_WSTR`||PMML 形式でのモデルのコンテンツの XML 表現。|  
|`SIZE`|`DBTYPE_UI4`||XML 文字列のバイト数。|  
|`LOCATION`|`DBTYPE_WSTR`||XML ファイルの場所。 格納に物理ファイルを使用しない場合は `NULL` です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 DMSCHEMA_MINING_MODEL_XML 行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_W`STR|任意。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|任意。|  
|`MODEL_NAME`|`DBTYPE_WSTR`|任意。|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
