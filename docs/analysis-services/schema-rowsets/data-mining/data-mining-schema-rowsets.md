---
title: データ マイニング スキーマ行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0324ee3b35f4b45162b9646d2d0e9cfeada47551
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="data-mining-schema-rowsets"></a>データ マイニング スキーマ行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [データ マイニング スキーマ行セット&#40;SSAs&#41;](../../../analysis-services/data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
