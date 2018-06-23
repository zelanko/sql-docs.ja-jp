---
title: データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e741f590755ebd032b7d26af8fe59772110578cf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173427"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>データ領域にデータがないことを示すメッセージの設定 (レポート ビルダーおよび SSRS)
  データのないデータ領域の代わりに表示レポートに表示するテキストを指定するときは、テーブル、マトリックス、または一覧データ領域に対して NoRowsMessage プロパティを、グラフ データ領域に対して NoDataMessage を、マップのカラー スケールに対して NoDataText を、それぞれ設定します。 実行時にレポート プロセッサによってレポートの各データセットに対しクエリが実行されますが、データセット クエリによって結果セットが生成されない場合があります。 空のデータセットにバインドされるデータ領域に対し、空のデータ領域を表示する代わりに表示するテキストを指定できます。 また、サブレポートのデータセットに実行時のデータがない場合、サブレポートに対し NoRowsMessage プロパティを設定することもできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>テーブル、マトリックス、リストに NoRowsMessage プロパティを設定するには  
  
1.  [デザイン] ビューで、デザイン画面のテーブル、マトリックス、一覧データ領域、またはサブレポートをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインでのメッセージとして表示するテキストを入力`NoRowsMessage`プロパティ フィールドです。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>グラフに NoDataMessage プロパティを設定するには  
  
1.  [デザイン] ビューで、デザイン画面のグラフをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインでノードを展開します`NoDataMessage`です。  
  
3.  **キャプション**、内のメッセージとして表示するテキストを入力`NoDataMessage`プロパティ フィールドです。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>サブレポートに NoRowsMessage を設定するには  
  
1.  [デザイン] ビューで、デザイン画面のサブレポートをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインでのメッセージとして表示するテキストを入力`NoRowsMessage`プロパティ フィールドです。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>マップのカラー スケールに NoDataText プロパティを設定するには  
  
1.  [デザイン] ビューで、マップのカラー スケールをクリックして選択します。 選択したアイテムのプロパティがプロパティ ペインに表示されます。  
  
2.  プロパティ ペインで `NoDataText`データ値を持たない色のラベルとして表示するテキストを入力します。  
  
     または、ドロップダウン リストから **[式]** をクリックして **[式]** ダイアログ ボックスを開き、式を作成します。  
  
## <a name="see-also"></a>参照  
 [サブレポート&#40;レポート ビルダーおよび SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md)   
 [マップ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md)   
 [サブレポート&#40;レポート ビルダーおよび SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)  
  
  