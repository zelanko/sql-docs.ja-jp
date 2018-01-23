---
title: "キューブのプロパティ - 多次元モデルのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d22d6fd46939b435cc0a8a6f25268aea0a192d6
ms.sourcegitcommit: 82c9868b5bf95e5b0c68137ba434ddd37fc61072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="cube-properties---multidimensional-model-programming"></a>キューブのプロパティ - 多次元モデルのプログラミング
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]キューブでは、キューブ全体の動作に影響する設定できるプロパティの数があります。 次の表は、これらのプロパティについてまとめたものです。  
  
> [!NOTE]  
>  キューブの作成時に自動的に設定され、変更できないプロパティもあります。  
  
 キューブのプロパティを設定する方法の詳細については、次を参照してください。[キューブ デザイナー &#40;です。Analysis Services - 多次元データ &#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**AggregationPrefix**|集計名に使用する共通のプレフィックスを指定します。|  
|**[照合順序]**|Latin1_General_C1_AS のように、アンダースコアで区切られたロケール識別子 (LCID) と比較フラグを指定します。|  
|**DefaultMeasure**|キューブの既定のメジャーを定義する多次元式 (MDX) 式を保持します。|  
|**Description**|キューブの説明を指定します。クライアント アプリケーションに公開できます。|  
|**ErrorConfiguration**|重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定を保持します。|  
|**EstimatedRows**|キューブ内の予測行数を指定します。|  
|**ID**|キューブの一意識別子 (ID) を保持します。|  
|**言語**|キューブの既定の言語識別子を指定します。|  
|**名前**|キューブの表示名を指定します。|  
|**ProactiveCaching**|キューブのプロアクティブ キャッシュ設定を定義します。|  
|**ProcessingMode**|インデックス作成と集計を処理中に行うか、処理後に行うかを指定します。 オプションは**正規**または**レイジー**です。|  
|**ProcessingPriority**|レイジー集計やインデックス作成など、バックグラウンド操作中のキューブの処理の優先度を決定します。 既定値は **0**です。|  
|**ScriptCacheProcessingMode**|スクリプト キャッシュのビルドを処理中に行うか、処理後に行うかを指定します。 オプションは**正規**と**レイジー**です。|  
|**ScriptErrorHandlingMode**|エラー処理を決定します。 オプションは**ignorenone です**または**ignoreall です**|  
|**ソース**|キューブに使用するデータ ソース ビューを表示します。|  
|**StorageLocation**|キューブのファイル システムでのストレージ場所を指定します。 指定しない場合は、キューブ オブジェクトが含まれているデータベースから場所が継承されます。|  
|**StorageMode**|キューブのストレージ モードを指定します。 値は**MOLAP**、 **ROLAP**、または**HOLAP**です。|  
|**[表示]**|キューブを表示するかどうかを決定します。|  
  
> [!NOTE]  
>  Null 値やその他のデータ整合性の問題を操作するとき、ErrorConfiguration プロパティの値の設定の詳細については、次を参照してください。 [Analysis Services 2005 でのデータの整合性問題の処理](http://go.microsoft.com/fwlink/?LinkId=81891)です。  
  
## <a name="see-also"></a>参照  
 [プロアクティブ キャッシュ (&) #40 です。パーティション&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
