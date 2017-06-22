---
title: "Reporting Services モバイル レポートを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e84dc855-aede-4fb4-b721-e6d8787961f4
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7fce4526bb296113aedb62e5dcf94b50e198210f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-reporting-services-mobile-report"></a>Reporting Services モバイル レポートの作成
SQL Server Mobile Report Publisher でをすばやく調整可能なグリッド行と列、および柔軟なモバイル レポート要素を使用して、デザイン サーフェイス上の任意の画面サイズにスケール アウトする SQL Server 2016 Reporting Services モバイル レポートを作成することができます。  
  
初めてのモバイル レポートを作成する Reporting Services web ポータルからローカル コンピューターに SQL Server Mobile Report Publisher をインストールできます。 または、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=733527)からインストールすることもできます。 2 回目以降は、Web ポータルまたはローカルのいずれかから開始できます。   
    
1. Reporting Services web ポータルの上部のバーで、選択**新規** > **モバイル レポート**です。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. **レイアウト**Mobile Report Publisher でタブをナビゲーター、ゲージ、グラフ、マップ、または datagrid を選択し、デザイン グリッドにドラッグします。  
  
3. 要素の右下隅をクリックし、希望のサイズにドラッグします。  
  
   ![SSMRP_ResizeChart](../../reporting-services/mobile-reports/media/ssmrp-resizechart.png)  
  
   これが、レポートに含める要素を作成する **マスター** デザイン グリッドです。 後で、 [タブレットまたはスマートフォン用にレポートをレイアウト](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)できます。     
     
   デザイン グリッドの下の **[ビジュアル プロパティ]** にさまざまなプロパティを設定することに注意してください。  
     
4. 左上隅の **[データ]** タブを選択すると、既にグラフにシミュレーションされたデータが関連付けられていることを確認できます。   
  
   ![SSMRP_SimTable](../../reporting-services/mobile-reports/media/ssmrp-simtable.png)  
  
5. 右上隅の **[データの追加]** を選択します。  
  
6. **[ローカル Excel]** または **[レポート サーバー]**を選択します。  
  
   >**ヒント**: Excel からデータを追加する場合、次を確認します。  
    >* モバイル レポートで作業できるよう、 [Excel データを準備します](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md) 。  
    >* まずファイルを閉じます。  
7. 目的のワークシートを選択し、 **[インポート]**を選択します。   
   ブックから一度に 1 つ以上のワークシートを追加できます。  
    
     ![SSMRP_AddExcelData](../../reporting-services/mobile-reports/media/ssmrp-addexceldata.png)  
  
8. 引き続き、 **[データ]** タブの **[データ プロパティ]** ボックスで、グラフに必要なテーブルとフィールドを選択します。  
  
   ![SSMRP_DataProps](../../reporting-services/mobile-reports/media/ssmrp-dataprops.png)  
  
9. **[レイアウト]** タブに戻り、 **[表示プロパティ]** ボックスで、 **[タイトル]**、 **[時間の単位]**、 **[数値書式]**などのプロパティを設定します。  
  
   ![SSMRP_ChartVizProps](../../reporting-services/mobile-reports/media/ssmrp-chartvizprops.png)  
    
10. 左上の **[プレビュー]** を選択し、レポートがどのように整形されたか確認します。  
  
11. 次にレポートを保存します。 左上隅の [保存] アイコンを選択して、 **[ローカルに保存]** または **[サーバーに保存]**を選択します。  
  
   サーバーに、保存するには、SQL Server 2016 Reporting Services レポート サーバーへのアクセスが必要です。  
     
   ### <a name="see-also"></a>参照  
     
-   [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-   [スマートフォンやタブレット向けに Reporting Services モバイル レポートをレイアウトする](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)  
  
   
