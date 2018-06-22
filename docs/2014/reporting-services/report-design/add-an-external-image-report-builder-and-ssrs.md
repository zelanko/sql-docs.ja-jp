---
title: 外部の画像の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 58875d6b3fd43962929096912d46f8157f02b77b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075445"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>外部の画像の追加 (レポート ビルダーおよび SSRS)
  外部の画像は、ネイティブ モードまたは SharePoint 統合モードのレポート サーバー上にあるものも、他の Web サイトにあるものもあります。 外部の画像をレポートに含める場合、その画像が存在すること、およびその画像にアクセスする権限をレポートのリーダーが持っていることを確認する必要があります。 詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](images-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>外部の画像を追加するには  
  
1.  レポート デザイン ビューの **[挿入]** タブで、 **[画像]** をクリックします。  
  
2.  デザイン画面で、ボックスをクリックし、画像の目的のサイズにドラッグします。  
  
3.  **[画像のプロパティ]** ダイアログ ボックスの **[全般]** タブにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。  
  
4.  (省略可) **[ツールヒント]** ボックスに、HTML で表示されたレポートの画像の上にマウスを置いたときに表示されるテキストを入力します。  
  
5.  **[画像ソースの選択]** で、 **[外部]** を選択します。  
  
     ネイティブ モードのレポート サーバーにある画像を指定する場合は、 **[次の画像を使用]** ボックスに画像の相対パスを入力します (例: ../images/image1.jpg)。  
  
     SharePoint 統合モードのレポート サーバーまたはその他の Web サイトにある画像を指定する場合は、**[次の画像を使用]** ボックスに画像への完全な URL を入力します (例: http://\<SharePoint サーバー名>/\<サイト>/Documents/images/image1.jpg)。  
  
     詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。  
  
6.  (省略可) 画像レポート アイテムのその他のプロパティを設定するには、 **[サイズ]**、 **[表示]**、 **[アクション]**、または **[罫線]** を選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [レポートに画像を埋め込む&#40;レポート ビルダーおよび SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-background-image-report-builder-and-ssrs.md)   
 [[全般] &#40;[画像のプロパティ] ダイアログ ボックス&#41; &#40;レポート ビルダーおよび SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  