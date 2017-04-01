---
title: "レポートへの HTML の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30bd631a-f774-48e7-a13a-b6c2eb54d9bb
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# レポートへの HTML の追加 (レポート ビルダーおよび SSRS)
  レポートでプレースホルダーを使用すると、データセットのフィールドから HTML をインポートできます。 既定のプレースホルダーはプレーン テキストを表すため、プレースホルダーのマークアップ タイプを HTML に変更する必要があります。 詳細については、[「レポートへの HTML のインポート (レポート ビルダーおよび SSRS)」](../../reporting-services/report-design/importing-html-into-a-report-report-builder-and-ssrs.md) を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### データセットのフィールドからテキスト ボックスに HTML を追加するには  
  
1.  **[挿入]** タブの **[一覧]** をクリックします。 デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。  
  
     **[データセットのプロパティ]** ダイアログ ボックスが表示されます。 共有データセットまたはレポートに埋め込まれたデータセットを使用できます。 詳細については、[[クエリ] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query%20\(Report%20Builder\).md) または [[クエリ] ([データセットのプロパティ] ダイアログ ボックス)](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query.md) をクリックしてください。  
  
2.  **[挿入]** タブの **[テキスト ボックス]** をクリックします。 一覧内をクリックし、次にマウスをドラッグして、必要なサイズのボックスを作成します。  
  
3.  データセットからテキスト ボックスに HTML フィールドをドラッグします。 フィールドに対してプレースホルダーが作成されます。  
  
4.  プレースホルダーを右クリックし、**[プレースホルダーのプロパティ]** をクリックします。  
  
5.  **[全般]** タブの **[値]** ボックスに、手順 3 でドロップしたフィールドを評価する式が入力されていることを確認します。  
  
6.  **[HTML - HTML タグをスタイルとして解釈]** をクリックします。 これで、フィールドが HTML として評価されます。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [数値と日付の書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [線、色、および画像の書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-lines-colors-and-images-report-builder-and-ssrs.md)   
 [[全般] ([プレースホルダーのプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../Topic/Placeholder%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  