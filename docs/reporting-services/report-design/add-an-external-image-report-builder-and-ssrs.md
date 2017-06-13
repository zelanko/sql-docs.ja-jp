---
title: "外部の画像 (レポート ビルダーおよび SSRS) の追加 |Microsoft ドキュメント"
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
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 291a906484a6f7d812d091252802b706d207a69e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>外部の画像の追加 (レポート ビルダーおよび SSRS)
  外部の画像は、ネイティブ モードまたは SharePoint 統合モードのレポート サーバー上にあるものも、他の Web サイトにあるものもあります。 外部の画像をレポートに含める場合、その画像が存在すること、およびその画像にアクセスする権限をレポートのリーダーが持っていることを確認する必要があります。 詳細については、「[画像 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>外部の画像を追加するには  
  
1.  レポート デザイン ビューの **[挿入]** タブで、 **[画像]**をクリックします。  
  
2.  デザイン画面で、ボックスをクリックし、画像の目的のサイズにドラッグします。  
  
3.  **[画像のプロパティ]** ダイアログ ボックスの **[全般]** タブにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。  
  
4.  (省略可) **[ツールヒント]** ボックスに、HTML で表示されたレポートの画像の上にマウスを置いたときに表示されるテキストを入力します。  
  
5.  **[画像ソースの選択]**で、 **[外部]**を選択します。  
  
     ネイティブ モードのレポート サーバーにある画像を指定する場合は、 **[次の画像を使用]** ボックスに画像の相対パスを入力します (例: ../images/image1.jpg)。  
  
     SharePoint 統合モード、またはその他の Web サイトでレポート サーバー上の画像のイメージに完全な URL を入力、**このイメージを使用**ボックス — たとえば、http://\<SharePointservername >/\<サイト >/Documents/images/image1.jpg です。  
  
     詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。  
  
6.  (省略可) 画像レポート アイテムのその他のプロパティを設定するには、**[サイズ]**、**[表示]**、**[アクション]**、または **[罫線]** を選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [レポートへの画像の埋め込み &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [[画像のプロパティ] ダイアログ ボックス &#40;レポート ビルダーおよび SSRS&#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
