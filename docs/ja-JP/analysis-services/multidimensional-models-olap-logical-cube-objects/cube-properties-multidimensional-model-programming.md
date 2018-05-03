---
title: キューブのプロパティ - 多次元モデルのプログラミング |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7dd5d6a976c21b7413b24ba59310cdd95c6fd13e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cube-properties---multidimensional-model-programming"></a>キューブのプロパティ - 多次元モデルのプログラミング
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブには、キューブ全体の動作に影響するように設定できる多数のプロパティがあります。 次の表は、これらのプロパティについてまとめたものです。  
  
> [!NOTE]  
>  キューブの作成時に自動的に設定され、変更できないプロパティもあります。  
  
 キューブのプロパティを設定する方法の詳細については、次を参照してください。[キューブ デザイナー &#40;Analysis Services - 多次元データ&#41;](http://msdn.microsoft.com/library/a6692467-da88-4312-8b03-d812f2ae5a96)です。  
  
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
 [プロアクティブ キャッシュ (&) #40 です。パーティション"&"#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)  
  
  
