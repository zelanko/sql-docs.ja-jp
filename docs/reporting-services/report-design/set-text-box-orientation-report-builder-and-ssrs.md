---
title: "テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、さまざまな方向にテキスト ボックスを回転することができます。   
* 水平方向   
* 垂直方向 (90 度回転。テキストの読み取りは上から下)  
* 270 度回転 (テキストの読み取りは下から上)   
  
回転するのはテキストではなくテキスト ボックスであるため、対象のテキスト ボックス内のすべてのテキストに回転が適用されます。 テキストの一部のみに異なる方向を指定することはできません。 回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。  
  
 テキストの向きを指定する WritingMode プロパティは、**[テキスト ボックスのプロパティ]** ダイアログ ボックスにはありません。 このプロパティはプロパティ ペインで設定できます。   
  
## テキストを回転するには  
  
1.  レポートを作成するか、または既存のレポートを開いてから、デザイン画面に[テキスト ボックスを追加](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md)します。  
  
3.  回転するテキスト ボックスを選択します。  
  
2.  プロパティ ペインが表示されていない場合は、**[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。  
  
4.  プロパティ ペインで、WritingMode プロパティを見つけて、テキスト ボックスに適用するテキストの向きを選択します。  
  
    > [!NOTE]  
    >  プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、**[ローカライズ]** カテゴリ内にあります。  
  
5.  リスト ボックスで **[横]**、 **[縦]**、 **[270 度回転]**のいずれかを選択します。  
  
## 参照  
 [テキスト ボックス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [チュートリアル: テキストの書式設定 (レポート ビルダー)](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  