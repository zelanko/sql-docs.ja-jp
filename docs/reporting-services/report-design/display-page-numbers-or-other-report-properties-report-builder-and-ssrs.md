---
title: ページ番号またはその他のレポート プロパティの表示 (レポート ビルダー) | Microsoft Docs
description: ページのヘッダーまたはフッターに表示するため、ページ番号、ファイル名、タイトルなど、レポートのプロパティを追加します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b5bd98f079ed492a4959597068c1f49a048b74cd
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689536"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a>ページ番号またはその他のレポート プロパティの表示 (レポート ビルダーおよび SSRS)
  レポートのページ ヘッダーまたはページ フッターにページ番号、レポート タイトル、ファイル名、およびその他のレポート プロパティを簡単に追加できます。 これらのプロパティは、レポート データ ペインの [組み込みフィールド] フォルダーのフィールドとして保存されます。  
  
-   [実行時間]  
  
-   ページ番号  
  
-   [レポート フォルダー]  
  
-   レポート名  
  
-   [レポート サーバー URL]  
  
-   [総ページ数]  
  
-   User ID  
  
-   Language  
  
 ページ番号については、番号の前に "ページ" という語を追加したり、 総ページ数を表示したりすることもできます。  
  
> [!NOTE]  
>  フッターに総ページ数を追加すると、レポートの実行時やプレビュー時にパフォーマンスが低下することがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a>ページ番号またはその他のレポート プロパティを追加するには  
  
1.  レポート データ ペインで [組み込みフィールド] フォルダーを展開します。  
  
    > [!NOTE]  
    >  [レポート データ] ペインが表示されていない場合は、[表示] タブの **[レポート データ]** をオンにします。  
  
2.  **[ページ番号]** フィールドを、[レポート データ] ペインからレポート ヘッダーまたはレポート フッターにドラッグします。  
  
    > [!NOTE]  
    >  ページ フッターはレポートに自動的に追加されます。 ページ ヘッダーを追加するには、 **[挿入]** タブで、 **[ヘッダー]** をクリックして **[ヘッダーの追加]** をクリックします。  
    >   
    >  [&PageNumber] という単純な式が含まれているテキスト ボックスが追加されます。  
  
### <a name="to-add-the-word-page-before-the-page-number"></a>ページ番号の前に "ページ" という語を追加するには  
  
1.  [&PageNumber] が含まれているテキスト ボックスを右クリックし、 **[式]** をクリックします。  
  
     **[式の設定:値]** テキスト ボックスに、=Globals!PageNumber という式が含まれています。  
  
2.  = (等号) の後ろにカーソルを置き、「 **"ページ " &** 」と入力します。  
  
     式は、="ページ "&Globals!PageNumber となります。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a>ページ番号の後ろに総ページ数を追加するには  
  
1.  式が含まれているテキスト ボックスを右クリックし、 **[式]** をクリックします。  
  
2.  式の末尾に「 **&"/"&** 」と入力します。  
  
3.  [カテゴリ] ペインで、 **[組み込みフィールド]** を展開し、 **[TotalPages]** をダブルクリックします。  
  
     式は、="ページ "&Globals!PageNumber &"/"&Globals!TotalPages となります。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
