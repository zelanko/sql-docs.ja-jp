---
title: "データ マイニング スキーマ行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad8ac453d1d299be98f3cb46496685063fd66576
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-schema-rowsets"></a>データ マイニング スキーマ行セット
  実行しているサーバー [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]次のデータ マイニング スキーマ行セットをサポートしています。 確認するには、特定の XML/A プロバイダーが特定の行セットをサポートしているかどうかを使用して、 [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)を含む行セット、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。  
  
 また、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] では、Transact-SQL 言語においてデータ マイニング スキーマ行セットが $SYSTEM スキーマのテーブルとして公開されます。 たとえば、Analysis Services インスタンスに対する次のクエリでは、現在のインスタンスで使用できるスキーマの一覧が返されます。  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|スキーマ行セット|Description|  
|-------------------|-----------------|  
|[DMSCHEMA_MINING_COLUMNS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|サーバー上に配置されているすべての定義済みデータ マイニング モデルの各列について記述します。|  
|[DMSCHEMA_MINING_FUNCTIONS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)|サーバーにインストールされている各データ マイニング アルゴリズムと共に使用できる予測関数およびマイニング関数について記述します。|  
|[DMSCHEMA_MINING_MODEL_CONTENT 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|クライアント アプリケーションでトレーニング済みのデータ マイニング モデルのコンテンツを参照できるようにします。|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)|マイニング モデルのコンテンツの XML (PMML 2.1) 表記を返します。|  
|[DMSCHEMA_MINING_MODEL_XML 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)|マイニング モデルの XML (PMML 2.1) 構造を返します。 旧バージョンとの互換性のために保持されている DMSCHEMA_MINING_MODEL_PMML と同じスキーマです。|  
|[DMSCHEMA_MINING_MODELS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|サーバー上に配置されているデータ マイニング モデルを列挙します。|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|サーバーにインストールされている各データ マイニング アルゴリズムの動作を構成するために使用できるパラメーターの一覧を提供します。|  
|[DMSCHEMA_MINING_SERVICES 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|サーバー上で使用できる各データ マイニング アルゴリズムについて記述します。|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|サーバー上に配置されているすべてのマイニング構造の各列について記述します。|  
|[DMSCHEMA_MINING_STRUCTURES 行セット](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|マイニング構造に関する情報を列挙します。|  
  
 ここで示すすべてのスキーマ行セットが実行されているサーバーでサポートされる[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)   
 [データ マイニング スキーマ行セット & #40 です。SSAs &#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  

