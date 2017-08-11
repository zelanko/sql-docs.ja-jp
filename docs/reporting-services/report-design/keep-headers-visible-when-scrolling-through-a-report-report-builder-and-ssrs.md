---
title: "(レポート ビルダーおよび SSRS) レポートのスクロール時にヘッダーを表示したまま |Microsoft ドキュメント"
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
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f2fac57fe0e898a1ccbfbe33fb271eae76da1389
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a>レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS)
  レポートを表示した後に、スクロールによって行ラベルや列ラベルが隠れないようにするために、行見出しまたは列見出しを固定できます。  
  
 行と列を制御する方法は、テーブルとマトリックスのどちらを使用しているかによって異なります。 テーブルを使用している場合は、静的メンバー (行見出しと列見出し) を表示したままにするよう構成します。 マトリックスを使用している場合は、行と列のグループ ヘッダーを表示したままにするよう構成します。  
  
 レポートを Excel にエクスポートしても、ヘッダーは自動的には固定表示されません。 Excel でウィンドウ枠を固定できます。 詳細については、次を参照してください、**ページ ヘッダーとフッター**のセクション[Microsoft Excel &#40; へのエクスポート。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  テーブルに行グループおよび列グループがある場合でも、スクロール中にこれらのグループ ヘッダーを表示したままにすることはできません。  
  
 次の図はテーブルを示しています。  
  
 ![テーブル](../../reporting-services/report-design/media/table.png "テーブル")  
  
 次の図はマトリックスを示しています。  
  
 ![マトリックス](../../reporting-services/report-design/media/matrix.png "マトリックス")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a>スクロール中もマトリックス グループ ヘッダーを表示したままにするには  
  
1.  Tablix データ領域の行、列、またはコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]**をクリックします。  
  
2.  **[全般]** タブの **[行のヘッダー]** または **[列のヘッダー]**で、 **[スクロール中もヘッダーを表示したままにする]**チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a>スクロール中も静的 Tablix メンバー (行または列) を表示したままにするには  
  
1.  デザイン画面でテーブル内の任意の場所をクリックし、グループ化ペインにグループと静的メンバーを表示します。  
  
     ![グループ化ペイン](../../reporting-services/report-design/media/grouppane-updated.png "グループ化ペイン")  
  
     行グループ ペインに、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示され、列グループ ペインに、列グループ階層のメンバーが同様に表示されます。  
  
2.  グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]**をクリックします。  
  
3.  スクロール中も表示したままにする静的メンバー (行または列) をクリックします。 プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。  
  
     ![Tablix メンバー プロパティ](../../reporting-services/report-design/media/grouppane-tablixmember-updated.png "Tablix メンバーのプロパティ")  
  
4.  プロパティ ペインで、 **[FixedData]** を **True**に設定します。  
  
5.  スクロール中も表示したままにするすべての隣接するメンバーに対して、この手順を繰り返します。  
  
6.  レポートをプレビューします。  
  
 レポートを下方向または横方向にスクロールしたときに、静的な Tablix メンバーが表示されたままになります。  
  
## <a name="see-also"></a>参照  
 [Tablix データ領域 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [検索、表示、およびレポート &#40; を管理します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [グループ &#40; でヘッダーとフッターを表示します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [複数のページ &#40; 行および列ヘッダーを表示します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [グループ化ペインと #40 です。レポート ビルダー"&"#41;](../../reporting-services/report-design/grouping-pane-report-builder.md)  
  
  
