---
title: クエリ (SQL Server データ マイニング アドイン) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [data mining]
- Data Mining Query Advanced Editor
- query builder [data mining]
- DMX
ms.assetid: 16af4a6f-18d4-496a-a304-7a13aa32ee76
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d2314c847745ac51d1bc7fb99b7c6f55a3f061af
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165335"
---
# <a name="query-sql-server-data-mining-add-ins"></a>クエリ (SQL Server データ マイニング アドイン)
  ![クエリ モデル ボタン、データ マイニング リボン](media/dmc-query.gif "クエリ モデル ボタン、データ マイニング リボン")  
  
 **クエリ**ウィザードを使用して、Excel テーブル、Excel 範囲、または別のデータ ソースのデータに基づいて予測を行う、既存のマイニング モデルと対話できます。 既存の傾向を予測するモデルに新しいデータを適用するプロセスが呼び出されると、*予測クエリ*です。  
  
 **クエリ**ウィザードは、作成またはデータ マイニング モデルを変更するため、カスタムのクエリを生成するため、または入れ子にされたデータセットなど、他のツールでサポートされていない構造を操作するためも高度なエディターを提供します。  
  
-   テキスト エディターを使用して、他の場所で作成したデータ マイニング拡張機能 (DMX) ステートメントを入力し貼り付けます。  
  
-   対話的なクエリ ビルダーを使用して、テンプレートとダイアログ ボックスの助けを借りて、カスタム DMX ステートメントを作成します。  
  
-   DMX ステートメントを作成して、マイニング モデルおよび構造を管理またはバックアップします。  
  
## <a name="using-the-query-wizard"></a>クエリ ウィザードの使用  
  
1.  最初に、入力として使用するデータ ソースを指定する必要があります。 既存の Excel テーブルまたは範囲のデータを使用できます。また、データを取得する SQL ステートメントを指定することもできます。  
  
2.  次に、接続しているサーバーのデータ マイニング モデルの一覧が表示されます。 データ マイニングに精通してモデルがわかっている場合も選択できます **[詳細設定]** を開くには、**データ マイニング詳細クエリ エディター**です。  
  
3.  選択したモデルの種類に応じて、評価するデータが格納されている列の指定、および入力データ列とモデル列のマッピングの定義を行う必要があります。 選択したアルゴリズムに応じて、モデルのその他のプロパティを設定する必要があります。  
  
4.  最後に、1 つまたは複数の予測を選択し、結果の保存先を指定します。  
  
 クリックして、いつでも**詳細**に切り替えるには、**データ マイニング詳細クエリ エディター**、DMX ステートメントの各部分をより詳細に制御を提供しています。 高度なクエリを編集ツールを使用する方法の詳細については、次を参照してください。[高度なデータ マイニングのクエリ エディター](advanced-data-mining-query-editor.md)です。  
  
### <a name="requirements"></a>要件  
 使用する、**クエリ**ウィザードのインスタンスに接続する必要がある必要があります[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 また、サーバーに適切な種類のデータ マイニング モデルが少なくとも 1 つ保存されている必要があります。 使用できるモデルが 1 つもない場合は、Excel 用のデータ マイニング クライアントのウィザードを使用して作成できます。 ウィザードを使用して新しいマイニング モデルを作成する方法については、次を参照してください。[データ マイニング モデルを作成する](creating-a-data-mining-model.md)です。  
  
## <a name="see-also"></a>参照  
 [展開して、マイニング モデルをスケーリング&#40;アドイン Excel 用データ マイニング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   
 [Excel 用データ マイニング クライアント&#40;SQL Server データ マイニング アドイン&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
  