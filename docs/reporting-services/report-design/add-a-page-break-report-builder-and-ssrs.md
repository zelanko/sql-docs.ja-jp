---
title: "改ページ (レポート ビルダーおよび SSRS) の追加 |Microsoft ドキュメント"
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
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81f305fdb34231a14c53d376ed9c4535ce6b9f53
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-page-break-report-builder-and-ssrs"></a>改ページの追加 (レポート ビルダーおよび SSRS)
  四角形、データ領域、またはデータ領域内のグループに改ページを追加して、各ページの情報量を制御することができます。 改ページを追加すると、レポートを表示する際に各ページのアイテムのみを処理すればよいので、パブリッシュされたレポートのパフォーマンスが向上します。 レポート全体が 1 ページで構成されている場合は、レポートを表示する前にすべてのアイテムを処理する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a>データ領域に改ページを追加するには  
  
1.  デザイン画面で、データ領域のコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]**をクリックします。  
  
2.  **[全般]** タブの **[改ページのオプション]**で、次のいずれかのオプションを選択します。  
  
    -   **[前に改ページを追加する]**: テーブルの前に改ページを追加する場合は、このチェック ボックスをオンにします。  
  
    -   **[後に改ページを追加する]**: テーブルの後に改ページを追加する場合は、このチェック ボックスをオンにします。  
  
    -   **[可能な場合は、テーブルを 1 ページに収める]**: データを 1 ページに収める場合は、このチェック ボックスをオンにします。  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a>四角形に改ページを追加するには  
  
1.  デザイン画面で、改ページを追加する四角形を右クリックし、 **[四角形のプロパティ]**をクリックします。  
  
2.  **[全般]** タブの **[改ページのオプション]**で、次のいずれかのオプションを選択します。  
  
    -   **[前に改ページを追加する]**: 四角形の前に改ページを追加する場合は、このチェック ボックスをオンにします。  
  
    -   **[後に改ページを追加する]**: 四角形の後に改ページを追加する場合は、このチェック ボックスをオンにします。  
  
    -   **[改ページの罫線を省略する]**: 改ページの罫線が不要な場合は、このチェック ボックスをオンにします。  
  
    -   **[可能な場合は、コンテンツを 1 ページに収める]**: 四角形内のコンテンツを 1 ページに収める場合は、このチェック ボックスをオンにします。  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a>テーブル、マトリックス、または一覧の行グループに改ページを追加するには  
  
1.  グループ化ペインで、行グループを右クリックし、 **[グループのプロパティ]**をクリックします。  
  
    > [!NOTE]  
    >  列グループでは改ページは無視されます。  
  
2.  **[改ページ]** タブの **[グループの各インスタンスの間]** を選択し、テーブル内のグループの各インスタンスの間に改ページを追加します。  
  
3.  必要に応じて、 **[グループの先頭でも改ページする]** チェック ボックスまたは **[グループの末尾でも改ページする]** チェック ボックスをオンにし、テーブル内のグループの開始時または終了時に改ページが追加されるよう指定します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services &#40; の改ページレポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [レンダリングの動作と #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [ページ ヘッダーとフッター & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
