---
title: テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6acffc286e913d35846b2eeb156cf1980b42fab3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104979"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>テキスト ボックスの方向の設定 (レポート ビルダーおよび SSRS)
  テキスト ボックスの方向には、水平、垂直 (テキストを上から下に配置)、または 270°回転 (テキストを下から上に配置) を使用できます。 方向はテキストではなくテキスト ボックスに設定されるため、そのテキスト ボックス内のすべてのテキストにその方向が適用されます。 テキストの一部のみに異なる方向を指定することはできません。 回転したテキストに合わせて、列の幅と行の高さを手動で調整してください。  
  
 テキストの向きを指定するために使用する WritingMode プロパティは、[**テキストボックスのプロパティ**] ダイアログボックスでは使用できません。 この場合、プロパティ ペインを開き、そこでプロパティを設定する必要があります。 WritingMode プロパティに使用できる値は、**水平**(左から右へのテキストの読み取り)、**縦**(テキストの上から下)、 **Rotate270** (テキストを下から上に読む) です。 テキストに合わせて、列の幅と行の高さを手動で調整する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>テキストの方向を指定する方法  
  
1.  レポートを新規作成するか、既存のレポートを開きます。  
  
2.  プロパティ ペインが表示されていない場合は、 **[表示]** タブの **[プロパティ]** チェック ボックスをオンにします。  
  
3.  変更を加えるテキスト ボックスをクリックし、テキスト ボックスの方向を変更します。  
  
4.  [プロパティ] ペインの [WritingMode] プロパティを見つけ、ドロップダウンリストで、テキストボックスに適用するテキストの方向を選択します。  
  
    > [!NOTE]  
    >  プロパティ ペインのプロパティがカテゴリごとに整理されている場合、WritingMode は、 **[ローカライズ]** カテゴリ内にあります。  
  
5.  リスト ボックスで **[横]** 、 **[縦]** 、 **[270 度回転]** のいずれかを選択します。  
  
## <a name="see-also"></a>参照  
 [テキスト ボックス &#40;レポート ビルダーおよび SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [チュートリアル: テキストの書式設定 &#40;レポート ビルダー&#41;](../tutorial-format-text-report-builder.md)  
  
  
