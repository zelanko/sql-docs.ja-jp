---
title: レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 42f5ca4942dc6d4a3e1d25805fffc2cd3e959860
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083804"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a>レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS)
  レポートを表示した後に、スクロールによって行ラベルや列ラベルが隠れないようにするために、行見出しまたは列見出しを固定できます。  
  
 行と列を制御する方法は、テーブルとマトリックスのどちらを使用しているかによって異なります。 テーブルを使用している場合は、静的メンバー (行見出しと列見出し) を表示したままにするよう構成します。 マトリックスを使用している場合は、行と列のグループ ヘッダーを表示したままにするよう構成します。  
  
 レポートを Excel にエクスポートしても、ヘッダーは自動的には固定表示されません。 Excel でウィンドウ枠を固定できます。 詳細については、「[Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)」の「**ページ ヘッダーとページ フッター**」を参照してください。  
  
> [!NOTE]  
>  テーブルに行グループおよび列グループがある場合でも、スクロール中にこれらのグループ ヘッダーを表示したままにすることはできません。  
  
 次の図はテーブルを示しています。  
  
 ![テーブル](../media/table.png "テーブル")  
  
 次の図はマトリックスを示しています。  
  
 ![マトリックス](../media/matrix.png "マトリックス")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a>スクロール中もマトリックス グループ ヘッダーを表示したままにするには  
  
1.  Tablix データ領域の行、列、またはコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。  
  
2.  **[全般]** タブの **[行のヘッダー]** または **[列のヘッダー]** で、 **[スクロール中もヘッダーを表示したままにする]** チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a>スクロール中も静的 Tablix メンバー (行または列) を表示したままにするには  
  
1.  デザイン画面でテーブル内の任意の場所をクリックし、グループ化ペインにグループと静的メンバーを表示します。  
  
     ![グループ化ペイン](../media/grouppane-updated.png "グループ化ペイン")  
  
     行グループ ペインに、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示され、列グループ ペインに、列グループ階層のメンバーが同様に表示されます。  
  
2.  グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]** をクリックします。  
  
3.  スクロール中も表示したままにする静的メンバー (行または列) をクリックします。 プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。  
  
     ![Tablix メンバー プロパティ](../media/grouppane-tablixmember-updated.png "Tablix メンバー プロパティ")  
  
4.  プロパティ ウィンドウで、次のように設定します。 **FixedData**に`True`です。  
  
5.  スクロール中も表示したままにするすべての隣接するメンバーに対して、この手順を繰り返します。  
  
6.  レポートをプレビューします。  
  
 レポートを下方向または横方向にスクロールしたときに、静的な Tablix メンバーが表示されたままになります。  
  
## <a name="see-also"></a>参照  
 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [レポートのエクスポート&#40;レポート ビルダーおよび SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)   
 [グループ単位でのヘッダーとフッターの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [グループ化ペイン &#40;レポート ビルダー&#41;](grouping-pane-report-builder.md)  
  
  