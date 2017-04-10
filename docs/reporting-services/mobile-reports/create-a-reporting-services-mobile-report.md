---
title: "Reporting Services モバイル レポートの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e84dc855-aede-4fb4-b721-e6d8787961f4
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Reporting Services モバイル レポートの作成
[!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] を使用すると、調整可能なグリッド行とグリッド列、柔軟なモバイル レポート要素を含むデザイン画面で、任意の画面サイズに対応する [!INCLUDE[PRODUCT_NAME](../../includes/sscurrent.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] モバイル レポートをすばやく作成できます。  
  
初めてモバイル レポートを作成するときは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] Web ポータルから [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] をローカル コンピューターにインストールできます。 または、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=733527)からインストールすることもできます。 2 回目以降は、Web ポータルまたはローカルのいずれかから開始できます。   
    
1. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] Web ポータルの上部のバーで、**[新規]** > **[モバイル レポート]** の順に選択します。  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] の **[レイアウト]** タブで、ナビゲーター、ゲージ、グラフ、マップ、またはデータグリッドを選択して、デザイン グリッドにドラッグします。  
  
3. 要素の右下隅をクリックし、希望のサイズにドラッグします。  
  
   ![SSMRP_ResizeChart](../../reporting-services/mobile-reports/media/ssmrp-resizechart.png)  
  
   これが、レポートに含める要素を作成する **マスター** デザイン グリッドです。 後で、[タブレットまたはスマートフォン用にレポートをレイアウト](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)できます。     
     
   デザイン グリッドの下の **[ビジュアル プロパティ]** にさまざまなプロパティを設定することに注意してください。  
     
4. 左上隅の **[データ]** タブを選択すると、既にグラフにシミュレーションされたデータが関連付けられていることを確認できます。   
  
   ![SSMRP_SimTable](../../reporting-services/mobile-reports/media/ssmrp-simtable.png)  
  
5. 右上隅の **[データの追加]** を選択します。  
  
6. **[ローカル Excel]** または **[レポート サーバー]** を選択します。  
  
   >**ヒント**: Excel からデータを追加する場合、次を確認します。  
    >* モバイル レポートで作業できるよう、[Excel データを準備します](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)。  
    >* まずファイルを閉じます。  
7. 目的のワークシートを選択し、**[インポート]** を選択します。   
   ブックから一度に 1 つ以上のワークシートを追加できます。  
    
     ![SSMRP_AddExcelData](../../reporting-services/mobile-reports/media/ssmrp-addexceldata.png)  
  
8. 引き続き、**[データ]** タブの **[データ プロパティ]** ボックスで、グラフに必要なテーブルとフィールドを選択します。  
  
   ![SSMRP_DataProps](../../reporting-services/mobile-reports/media/ssmrp-dataprops.png)  
  
9. **[レイアウト]** タブに戻り、**[表示プロパティ]** ボックスで、**[タイトル]**、**[時間の単位]**、**[数値書式]** などのプロパティを設定します。  
  
   ![SSMRP_ChartVizProps](../../reporting-services/mobile-reports/media/ssmrp-chartvizprops.png)  
    
10. 左上の **[プレビュー]** を選択し、レポートがどのように整形されたか確認します。  
  
11. 次にレポートを保存します。 左上隅の [保存] アイコンを選択して、**[ローカルに保存]** または **[サーバーに保存]** を選択します。  
  
   サーバーに保存するには、[!INCLUDE[PRODUCT_NAME](../../includes/sscurrent.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] レポート サーバーにアクセスできる必要があります。  
     
   ### 参照  
     
-   [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-   [スマートフォンやタブレット向けに Reporting Services モバイル レポートをレイアウトする](../../reporting-services/mobile-reports/lay-out-a-reporting-services-mobile-report-for-phone-or-tablet.md)  
  
   