---
title: "テキスト ボックスの方向 (レポート ビルダーおよび SSRS) の設定 |Microsoft ドキュメント"
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
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4cc52b4687f9a2c944ea3a93c15b637d894c7a96
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、さまざまな方向にテキスト ボックスを回転することができます。   
* 水平方向   
* 垂直方向 (90 度回転。テキストの読み取りは上から下)  
* 270 度回転 (テキストの読み取りは下から上)   
  
回転するのはテキストではなくテキスト ボックスであるため、対象のテキスト ボックス内のすべてのテキストに回転が適用されます。 テキストの一部のみに異なる方向を指定することはできません。 回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。  
  
 テキストの向きを指定する WritingMode プロパティは、 **[テキスト ボックスのプロパティ]** ダイアログ ボックスにはありません。 このプロパティはプロパティ ペインで設定できます。   
  
## <a name="to-rotate-text"></a>テキストを回転するには  
  
1.  レポートを作成するか、または既存のレポートを開いてから、デザイン画面に [テキスト ボックスを追加](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) します。  
  
3.  回転するテキスト ボックスを選択します。  
  
2.  プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。  
  
4.  プロパティ ペインで、WritingMode プロパティを見つけて、テキスト ボックスに適用するテキストの向きを選択します。  
  
    > [!NOTE]  
    >  プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。  
  
5.  リスト ボックスで **[横]**、 **[縦]**、 **[270 度回転]**のいずれかを選択します。  
  
## <a name="see-also"></a>参照  
 [テキスト ボックス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [チュートリアル: テキストの書式設定 &#40;です。レポート ビルダー&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
