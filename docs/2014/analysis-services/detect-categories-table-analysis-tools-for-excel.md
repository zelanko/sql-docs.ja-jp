---
title: カテゴリ (Excel 用テーブル分析ツール) の検出 |Microsoft ドキュメント
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
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d46840e2c2f7de1d56d6b528706ae908e7627a3e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076089"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>カテゴリの検出 (Excel 用のテーブル分析ツール)
  ![リボンの [カテゴリ] ボタンを検出](media/tat-detectcat.gif "リボン カテゴリの検出 ボタン")  
  
 **カテゴリの検出**ツールは自動的に類似の特性を持つテーブルの行を検索します。  
  
 このツールの処理が完了すると、検出されたカテゴリおよびその特徴を示すレポートが作成されます。 既定では、データの行ごとに、検出されたカテゴリを含む新しい列がデータ テーブルに追加されます。 後でそのカテゴリを確認し、名前を変更することができます。  
  
## <a name="using-the-detect-categories-tool"></a>カテゴリの検出ツールの使用  
  
1.  Excel テーブルを開きます。  
  
2.  をクリックして**カテゴリの検出**です。  
  
3.  分析に使用する列を指定します。 個人名やレコード ID などの一意な値を含む列は分析に役立たないため、選択を外すことができます。  
  
4.  作成するカテゴリの最大数を指定することもできます。 既定では、検出された数のカテゴリが自動的に作成されます。  
  
5.  **[実行]** をクリックします。  
  
6.  カテゴリとその特性の一覧が記載された "カテゴリのレポート" という名前の新規ワークシートが作成されます。  
  
 ツールのオプションを指定する方法の詳細については、次を参照してください。[検出カテゴリ ダイアログ ボックス (Excel 用テーブル分析ツール)](detect-categories-table-analysis-tools-for-excel.md)です。  
  
## <a name="understanding-the-categories-report"></a>カテゴリのレポートについて  
 **カテゴリのレポート**2 つのテーブルを含む**カテゴリの一覧**と**カテゴリの特性**、および**カテゴリ プロファイル**グラフ。  
  
### <a name="category-list"></a>カテゴリの一覧  
 最初のテーブルは、検出されたカテゴリを示します。 **行カウント**列は、データの行の数は、各カテゴリに割り当てられたことを示します。  
  
 モデルは、各カテゴリに対応する一時的な名前を作成しますが、カテゴリを好みの名前に変更することもできます。 たとえば、次の例では、最初のカテゴリ名前が変更された**低収入**でクラスターの最も重要な属性があるためです。  
  
 ![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report1.gif "カテゴリの検出ツールによって作成されたレポート")  
  
 新しいラベルを入力するとすぐに、その他のすべてのグラフのほかに、ソース データのワークシートに追加されたカテゴリの一覧にも反映されます。  
  
### <a name="category-characteristics"></a>カテゴリの特性  
 2 番目のテーブルでは、**カテゴリの特性**、各カテゴリの構成の詳細を表示します。 をクリックして、**フィルター**の上部にあるボタン、**カテゴリ**列を 1 つまたは少数のカテゴリのフォーカスを参照してください。  
  
 ![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report2.gif "カテゴリの検出ツールによって作成されたレポート")  
  
 列で、網掛け**相対的な重要度**、ことを示します属性と値の組み合わせが特徴的要因としてがある重要な方法です。 バーが長いほど、そのカテゴリの代表的な属性である可能性が高くなります。  
  
### <a name="categories-profile-chart"></a>カテゴリ プロファイル グラフ  
 最後のグラフで、**カテゴリのレポート**ワークシート、**カテゴリ プロファイル**は、対話型**ピボット グラフ**再配置し、フィールドを非表示、値のフィルター処理に使用できます。、およびグラフの外観をカスタマイズします。  
  
 Excel 2013 は、**グラフのスタイルを**と**グラフ要素**グラフのデザインが向上しやすいデザイン画面の右側を制御します。  
  
 ![カテゴリの検出ツールによって作成されたレポート](media/dm13-tat-detectcat-report3.gif "カテゴリの検出ツールによって作成されたレポート")  
  
## <a name="requirements"></a>要件  
 **カテゴリの検出**ツール量やデータの種類の要件はありません。  
  
> [!NOTE]  
>  使用すると、**カテゴリの検出**ツール、カテゴリで、新しい列で作成元のデータ テーブルです。 データ テーブルにこの列を残したままデータ マイニング処理を実行すると、この列が結果に影響することがあります。 他の処理に影響を及ぼさないようにするために、他のデータ マイニング ツールを使用する前に "カテゴリ" 列を含まないデータ テーブルのコピーを作成しておく必要があります。  
  
## <a name="related-tools"></a>関連ツール  
 ときに、**カテゴリの検出**ツールは、データを分析しを使用して、データ マイニング構造とデータ マイニング モデルを作成、[!INCLUDE[msCoName](../includes/msconame-md.md)]クラスタ リング アルゴリズムです。  
  
 使用して、データ マイニング モデルを作成した後、**分析の主要な影響元**ツールでモデルを参照しての詳細関係を調査する Excel 用データ マイニング クライアントを使用することができます。 Excel 用のデータ マイニング クライアントは、より詳細なデータ マイニング機能を備えた独立したアドインです。 詳細については、次を参照してください。 [Excel におけるモデルの参照&#40;SQL Server データ マイニング アドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)です。  
  
 詳細については、データ モデリング、Excel 用データ マイニング クライアントでの機能を使用して、次を参照してください。[データ マイニング モデルを作成する](creating-a-data-mining-model.md)です。  
  
 使用されるアルゴリズムの詳細については、**カテゴリの検出**ツール、トピックの「Microsoft クラスタ リング アルゴリズム」を参照してください[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [Excel 用テーブル分析ツール](table-analysis-tools-for-excel.md)  
  
  