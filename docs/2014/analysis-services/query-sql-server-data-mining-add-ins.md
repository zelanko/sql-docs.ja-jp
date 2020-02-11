---
title: クエリ (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dcddeb64b14301f08a7dc723ef89737102f257ad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070480"
---
# <a name="query-sql-server-data-mining-add-ins"></a>クエリ (SQL Server データ マイニング アドイン)
  ![[データ マイニング] リボンの [クエリ モデル] ボタン](media/dmc-query.gif "[データ マイニング] リボンの [クエリ モデル] ボタン")  
  
 **クエリ**ウィザードを使用すると、既存のマイニングモデルを操作して、excel テーブル、excel 範囲、または別のデータソースのデータに基づいて予測を行うことができます。 既存のモデルに新しいデータを適用して傾向を予測するプロセスを、*予測クエリ*と呼びます。  
  
 **クエリ**ウィザードでは、データマイニングモデルの作成または変更、カスタムクエリの生成、または入れ子になったデータセットなどの他のツールでサポートされていない構造の操作を行うための高度なエディターも用意されています。  
  
-   テキストエディターを使用して、他の場所で作成したデータマイニング拡張機能 (DMX) ステートメントを入力するか、貼り付けます。  
  
-   対話的なクエリ ビルダーを使用して、テンプレートとダイアログ ボックスの助けを借りて、カスタム DMX ステートメントを作成します。  
  
-   DMX ステートメントを作成して、マイニング モデルおよび構造を管理またはバックアップします。  
  
## <a name="using-the-query-wizard"></a>クエリ ウィザードの使用  
  
1.  最初に、入力として使用するデータ ソースを指定する必要があります。 既存の Excel テーブルまたは範囲のデータを使用できます。また、データを取得する SQL ステートメントを指定することもできます。  
  
2.  次に、接続しているサーバーのデータ マイニング モデルの一覧が表示されます。 必要なモデルがわかっていて、データマイニングに精通している場合は、[**詳細設定**] をクリックして、**データマイニング詳細クエリエディター**を開くこともできます。  
  
3.  選択したモデルの種類に応じて、評価するデータが格納されている列の指定、および入力データ列とモデル列のマッピングの定義を行う必要があります。 選択したアルゴリズムに応じて、モデルのその他のプロパティを設定する必要があります。  
  
4.  最後に、1 つまたは複数の予測を選択し、結果の保存先を指定します。  
  
 いつでも、[**詳細設定**] をクリックして**データマイニング詳細クエリエディター**に切り替えることができます。これにより、DMX ステートメントの各部分をより細かく制御できます。 高度なクエリ編集ツールの使用方法の詳細については、「[高度なデータマイニングクエリエディター](advanced-data-mining-query-editor.md)」を参照してください。  
  
### <a name="requirements"></a>必要条件  
 **クエリ**ウィザードを使用するには、の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスに接続されている必要があります。 また、サーバーに適切な種類のデータ マイニング モデルが少なくとも 1 つ保存されている必要があります。 使用できるモデルが 1 つもない場合は、Excel 用のデータ マイニング クライアントのウィザードを使用して作成できます。 ウィザードを使用して新しいマイニングモードを作成する方法については、「[データマイニングモデルの作成](creating-a-data-mining-model.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   
 [Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  
