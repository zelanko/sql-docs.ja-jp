---
title: "テキスト ボックス (レポート ビルダーおよび SSRS) 内のテキストの書式を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab1c264ec07230bd81769ab2886177552095e636
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a>テキスト ボックス内のテキストの書式設定 (レポート ビルダーおよび SSRS)
  テキスト ボックス内のテキストは、どの部分も個別に書式設定できます。また、1 つのテキスト ボックスに、プレースホルダー テキストと静的テキストを混在させることができます。 複数の書式を混在させ、プレースホルダー テキストを追加できるこの機能により、文書の差し込みを行ったり、レポート内のテキストに使用するテンプレートを作成したりできます。 プレースホルダーを使用することによって、あらゆる式を定義できるほか、それぞれの式に対して、個別に書式を適用することもできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a>テキスト ボックスで複数の書式を混在させるには  
  
1.  **[挿入]** タブの **[テキスト ボックス]**をクリックします。 デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。  
  
2.  テキスト ボックス内で、書式設定の対象となるテキストを選択します。  
  
3.  選択したテキストを右クリックして、 **[テキストのプロパティ]**をクリックします。  
  
4.  書式設定オプションを設定します。 たとえば、 **[全般]** タブには次のオプションがあります。  
  
    -   **[ツールヒント]** : テキスト、または結果がツールヒントになる式を入力します。 ツールヒントは、ユーザーがレポートのアイテムの上にポインターを置いたときに表示されます。  
  
    -   **[マークアップの種類]** : 選択したテキストの表示方法を指定するオプションを選択します。  
  
         **[テキスト形式]** : 選択したテキストを単純なテキストとして表示します。 HTML はリテラル テキストとして処理されます。  
  
         **[HTML]**  : 選択したテキストを HTML として表示します。 プレースホルダーの式の値が有効な HTML タグを含んでいる場合、これらのタグは HTML として表示されます。 詳細については、「[レポートへの HTML のインポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/importing-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
5.  **[OK]**をクリックします。  
  
6.  書式設定の対象となるその他のテキストについても、手順 2. ～ 5. を繰り返します。  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a>同じテキスト ボックス内のテキストとプレースホルダーの書式を個別に設定するには  
  
1.  **[挿入]** タブの **[一覧]**をクリックします。 デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。 **[データセットのプロパティ]** ダイアログ ボックスが表示されます。 共有データセットまたはレポートに埋め込まれたデータセットを使用できます。 詳細については、[[クエリ] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md) または [[クエリ] ([データセットのプロパティ] ダイアログ ボックス)](http://msdn.microsoft.com/library/1fa34a4b-7de0-4e92-99fa-bc28a206773f) をクリックしてください。  
  
2.  **[挿入]** タブの **[テキスト ボックス]** をクリックします。 一覧内をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。  
  
3.  テキスト ボックスのラベルを入力します。たとえば、「 **My Field**」と入力します。  
  
4.  データセットからテキスト ボックスにフィールドをドラッグします。 フィールドに対してプレースホルダーが作成されます。  
  
5.  基本的な書式設定の場合は、プレースホルダー テキストを選択し、 **[ホーム]** タブの **[フォント]** グループにある書式設定オプションのいずれかをクリックします。 たとえば、 **[太字]** ボタンをクリックします。  
  
     詳細な書式設定オプションの場合は、プレースホルダー テキストを右クリックし、 **[プレースホルダー プロパティ]**をクリックします。  
  
6.  **[OK]**をクリックします。 レポート デザイン ビューで、テキスト ボックスに "**My Field**: [*FieldName*]" と表示されます ( *FieldName* はフィールド名)。  
  
7.  **[実行]**をクリックします。  
  
 一覧はフィールド内の値ごとに 1 回繰り返され、プレースホルダー *FieldName* がデータセット内のそのフィールドの値に置き換わります。  
  
## <a name="see-also"></a>参照  
 [テキスト ボックスと &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [書式設定のテキストとプレース ホルダーと &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [レポートと &#40; 内の式の使用レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [レポートと &#40; に HTML を追加します。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/add-html-into-a-report-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、およびリスト &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [書式の数値および日付 &#40; です。レポート ビルダーおよび SSRS & &#41; です。](../../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [プレース ホルダーのプロパティ」 ダイアログ ボックス、全般、&#40; です。レポート ビルダーおよび SSRS &#41; です。](http://msdn.microsoft.com/library/7a867736-a3b0-4b5a-b3e5-fe7c8d7618a8)  
  
  
