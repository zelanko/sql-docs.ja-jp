---
title: "キューブのプロパティ - 多次元モデルのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b86278422fc1e3ec91845c223adc56640602739
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cube-properties---multidimensional-model-programming"></a>キューブのプロパティ - 多次元モデルのプログラミング
  キューブには、キューブ全体の動作に影響するように設定できる多数のプロパティがあります。 次の表は、これらのプロパティについてまとめたものです。  
  
> [!NOTE]  
>  キューブの作成時に自動的に設定され、変更できないプロパティもあります。  
  
 キューブのプロパティを設定する方法の詳細については、次を参照してください。[キューブ デザイナー &#40;です。Analysis Services - 多次元データ &#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96).  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**AggregationPrefix**|集計名に使用する共通のプレフィックスを指定します。|  
|**照合順序**|Latin1_General_C1_AS のように、アンダースコアで区切られたロケール識別子 (LCID) と比較フラグを指定します。|  
|**DefaultMeasure**|キューブの既定のメジャーを定義する多次元式 (MDX) 式を保持します。|  
|**Description**|キューブの説明を指定します。クライアント アプリケーションに公開できます。|  
|**ErrorConfiguration**|重複するキー、不明なキー、エラーの制限、エラー検出時のアクション、エラー ログ ファイル、および NULL キーを処理するための、構成可能なエラー処理設定を保持します。|  
|**EstimatedRows**|キューブ内の予測行数を指定します。|  
|**ID**|キューブの一意識別子 (ID) を保持します。|  
|**言語**|キューブの既定の言語識別子を指定します。|  
|**名前**|キューブの表示名を指定します。|  
|**プロアクティブ キャッシュ**|キューブのプロアクティブ キャッシュ設定を定義します。|  
|**ProcessingMode**|インデックス作成と集計を処理中に行うか、処理後に行うかを指定します。 オプションは**正規**または**レイジー**です。|  
|**ProcessingPriority**|レイジー集計やインデックス作成など、バックグラウンド操作中のキューブの処理の優先度を決定します。 既定値は **0**です。|  
|**ScriptCacheProcessingMode**|スクリプト キャッシュのビルドを処理中に行うか、処理後に行うかを指定します。 オプションは**正規**と**レイジー**です。|  
|**ScriptErrorHandlingMode**|エラー処理を決定します。 オプションは**ignorenone です**または**ignoreall です**|  
|**ソース**|キューブに使用するデータ ソース ビューを表示します。|  
|**[StorageLocation]**|キューブのファイル システムでのストレージ場所を指定します。 指定しない場合は、キューブ オブジェクトが含まれているデータベースから場所が継承されます。|  
|**StorageMode**|キューブのストレージ モードを指定します。 値は**MOLAP**、 **ROLAP**、または**HOLAP * * *。**|  
|**[表示]**|キューブを表示するかどうかを決定します。|  
  
> [!NOTE]  
>  Null 値やその他のデータ整合性の問題を操作するとき、ErrorConfiguration プロパティの値の設定の詳細については、次を参照してください。 [Analysis Services 2005 でのデータの整合性問題の処理](http://go.microsoft.com/fwlink/?LinkId=81891)です。  
  
## <a name="see-also"></a>参照  
 [プロアクティブ キャッシュ (&) #40 です。パーティション&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  

