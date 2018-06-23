---
title: クエリ バインドの詳細 ([パーティション ソース] ダイアログ ボックス) (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e9a9fc76282ebd231e18aec24fe6a9d28650100
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178754"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>クエリ バインドの詳細 ([パーティション ソース] ダイアログ ボックス) (Analysis Services - 多次元データ)
  **[パーティション ソース]** ダイアログ ボックスの **[クエリ バインド]** オプションを使用すると、パーティション用のデータを表示するクエリを指定できます。 このペインを表示するには、 **[パーティション ソース]** ダイアログ ボックスの **[バインドの種類]** オプションで **[クエリ バインド]** を選択します。  
  
## <a name="options"></a>および  
 **データ ソース**  
 パーティションのファクト データを提供するためのクエリが実行されるデータ ソースを選択します。  
  
 **クエリ**  
 パーティションを処理する際にファクト データの取得に使用される SQL ステートメントを入力、または変更します。  
  
> [!IMPORTANT]  
>  WHERE 句を指定することにより、レコードのサブセットをこのパーティションで使用できます。 複数のパーティションが 1 つのファクト テーブルに基づいている場合は、データを複製しないでください。 詳細については、次を参照してください。[パーティション ソース ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)です。  
  
 **[確認]**  
 クリックすると、 **クエリ** 内のステートメントが有効な SQL ステートメントであるかどうかが確認されます。  
  
## <a name="see-also"></a>参照  
 [パーティション ソース ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  