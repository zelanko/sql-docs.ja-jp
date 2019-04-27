---
title: Analysis Services 表形式モデルのテーブルまたは列を名前の変更 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e5c0173de2ea22e91c0a1f13517a9bcb7c58ed9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472181"
---
# <a name="rename-a-table-or-column"></a>テーブルまたは列名の変更 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  **テーブルのインポート ウィザード** の **[テーブルとビューの選択]** ページで **表示名**を入力することにより、インポート処理中にテーブルの名前を変更できます。 **テーブルのインポート ウィザード** の **[SQL クエリの指定]** ページでクエリを指定してデータをインポートした場合は、テーブルおよび列の名前を変更することもできます。  
  
 データをモデルに追加すると、テーブルの名前 (つまりタイトル) がモデル デザイナーの下部にあるテーブル タブに表示されます。 テーブルの名前は、より適切な名前に変更できます。 列の名前は、データをモデルに追加した後で変更することもできます。 このオプションは、複数のソースからデータをインポートして、別のテーブルの列にわかりやすい名前を付けたい場合に特に重要となります。  
  
### <a name="to-rename-a-table"></a>テーブル名を変更するには  
  
1.  モデル デザイナーで、名前を変更するテーブルが入っているタブを右クリックして、 **[名前の変更]** をクリックします。  
  
2.  新しい名前を入力します。  
  
    > [!NOTE]  
    >  **[テーブルのプロパティの編集]** ダイアログ ボックスを使用すると、接続情報や列マッピングなど、名前以外のテーブルのプロパティを編集できます。 ただし、このダイアログ ボックスでは、名前を変更できません。  
  
### <a name="to-rename-a-column"></a>列名を変更するには  
  
1.  モデル デザイナーで名前を変更する列の見出しをダブルクリックするか、見出しを右クリックし、コンテキスト メニューの **[列名の変更]** をクリックします。  
  
2.  新しい名前を入力します。  
  
## <a name="naming-requirements-for-columns-and-tables"></a>列とテーブルの名前付けに関する要件  
 次の単語と文字をテーブルまたは列の名前で使用することはできません。  
  
-   先頭または末尾の空白。  
  
-   制御文字。  
  
-   (これは、Analysis Services オブジェクトの名前に無効な) 次の文字:.、;'/。\\*|?& % $! + = (){}<>  
  
-   Analysis Services の予約済みキーワード。多次元式 (MDX) とデータ マイニング拡張機能 (DMX) の関数名と演算子を含みます。  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a>既存のテーブル、列、および計算名を変更することによる影響  
 テーブルの名前を変更するたびに、基になるテーブル オブジェクトの名前も変更されます。このテーブル オブジェクトには複数の列またはメジャーが含まれていることがあります。 その定義で、新しい名前を使用する、テーブル内にあるすべての列とテーブルを使用するすべてのリレーションシップを更新する必要があります。 ほとんどの場合は、この更新プログラムが自動的に行われます。
  
 名前が変更されたテーブルを使用するか、名前を変更したテーブルから列を使用する計算も更新する必要があります、およびこれらの計算から派生したデータの更新し再計算する必要があります。 影響を受けるテーブルと計算の数によっては、完了までに時間がかかることがあります。 このため、テーブル名を変更するタイミングとしては、インポート処理時か、複雑なリレーションシップや計算を構築する前が最適です。  
  
## <a name="see-also"></a>参照  
 [テーブルと列](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [Power Pivot からのインポート](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Analysis Services からのインポート](../../analysis-services/tabular-models/import-from-analysis-services-ssas-tabular.md)  
  
  
