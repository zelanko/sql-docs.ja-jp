---
title: テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cc2ef22253eaef7c86eeee43ed0260d24d3adfe4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178392"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)
  テキスト ボックスの方向には、水平、垂直 (テキストを上から下に配置)、または 270°回転 (テキストを下から上に配置) を使用できます。 方向はテキストではなくテキスト ボックスに設定されるため、そのテキスト ボックス内のすべてのテキストにその方向が適用されます。 テキストの一部のみに異なる方向を指定することはできません。 回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。  
  
 テキストの向きを指定するために使用、WritingMode プロパティでは使用できません、**テキスト ボックスのプロパティ** ダイアログ ボックス。 この場合、プロパティ ペインを開き、そこでプロパティを設定する必要があります。 WritingMode プロパティの使用できる値は**水平**(テキストを読める左から右)、**垂直**(文字の上下からへの読み取り)、 **Rotate270** (テキストの読み取り下から上)。 テキストに合わせて、列の幅と行の高さを手動で調整する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>テキストの方向を指定する方法  
  
1.  レポートを新規作成するか、既存のレポートを開きます。  
  
2.  プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。  
  
3.  変更を加えるテキスト ボックスをクリックし、テキスト ボックスの方向を変更します。  
  
4.  プロパティ ペインで、ドロップダウン リストでのプロパティは、テキスト ボックスに適用するテキストの向きを選択します。 WritingMode を見つけます。  
  
    > [!NOTE]  
    >  プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。  
  
5.  リスト ボックスで **[横]**、 **[縦]**、 **[270 度回転]** のいずれかを選択します。  
  
## <a name="see-also"></a>参照  
 [テキスト ボックス&#40;レポート ビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [チュートリアル: テキストの書式設定 &#40;レポート ビルダー&#41;](../tutorial-format-text-report-builder.md)  
  
  