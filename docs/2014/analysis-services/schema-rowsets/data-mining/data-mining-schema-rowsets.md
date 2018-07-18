---
title: データ マイニング スキーマ行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- schema rowsets [Analysis Services]
- rowsets [Analysis Services], data mining
- data mining [Analysis Services], schema rowsets
ms.assetid: bd7d5df5-500b-4159-8467-880e141bc043
caps.latest.revision: 43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a3b3e54f53eb93ea58a45c92e88503a186a441f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210052"
---
# <a name="data-mining-schema-rowsets"></a>データ マイニング スキーマ行セット
  実行しているサーバー [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]次のデータ マイニング スキーマ行セットをサポートしています。 特定の XML/A プロバイダーが特定の行セットをサポートしているかどうかを確認するには、使用、 [DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md)を含む行セット、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッド。  
  
 また、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] では、Transact-SQL 言語においてデータ マイニング スキーマ行セットが $SYSTEM スキーマのテーブルとして公開されます。 たとえば、Analysis Services インスタンスに対する次のクエリでは、現在のインスタンスで使用できるスキーマの一覧が返されます。  
  
```  
SELECT * FROM [$system].[DBSCHEMA_TABLES]  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|スキーマ行セット|説明|  
|-------------------|-----------------|  
|[DMSCHEMA_MINING_COLUMNS 行セット](dmschema-mining-columns-rowset.md)|サーバー上に配置されているすべての定義済みデータ マイニング モデルの各列について記述します。|  
|[DMSCHEMA_MINING_FUNCTIONS 行セット](dmschema-mining-functions-rowset.md)|サーバーにインストールされている各データ マイニング アルゴリズムと共に使用できる予測関数およびマイニング関数について記述します。|  
|[DMSCHEMA_MINING_MODEL_CONTENT 行セット](dmschema-mining-model-content-rowset.md)|クライアント アプリケーションでトレーニング済みのデータ マイニング モデルのコンテンツを参照できるようにします。|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML 行セット](dmschema-mining-model-content-pmml-rowset.md)|マイニング モデルのコンテンツの XML (PMML 2.1) 表記を返します。|  
|[DMSCHEMA_MINING_MODEL_XML 行セット](dmschema-mining-model-xml-rowset.md)|マイニング モデルの XML (PMML 2.1) 構造を返します。 旧バージョンとの互換性のために保持されている DMSCHEMA_MINING_MODEL_PMML と同じスキーマです。|  
|[DMSCHEMA_MINING_MODELS 行セット](dmschema-mining-models-rowset.md)|サーバー上に配置されているデータ マイニング モデルを列挙します。|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS 行セット](dmschema-mining-service-parameters-rowset.md)|サーバーにインストールされている各データ マイニング アルゴリズムの動作を構成するために使用できるパラメーターの一覧を提供します。|  
|[DMSCHEMA_MINING_SERVICES 行セット](dmschema-mining-services-rowset.md)|サーバー上で使用できる各データ マイニング アルゴリズムについて記述します。|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット](dmschema-mining-structure-columns-rowset.md)|サーバー上に配置されているすべてのマイニング構造の各列について記述します。|  
|[DMSCHEMA_MINING_STRUCTURES 行セット](dmschema-mining-structures-rowset.md)|マイニング構造に関する情報を列挙します。|  
  
 次のとおり、すべてのスキーマ行セットを実行しているサーバーでサポートされる[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)   
 [SQL Server のシステム カタログに対するクエリ](https://technet.microsoft.com/en-us/library/ms189082\(v=sql.110\).aspx)   
 [データ マイニング スキーマ行セット クエリ&#40;Analysis Services - データ マイニング&#41;](../../data-mining/data-mining-schema-rowsets-ssas.md)  
  
  
