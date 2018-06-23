---
title: レポートへの罫線の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 4295a712f277047c4e205d83c44bbc0ff444db32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177250"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a>レポートへの罫線の追加 (レポート ビルダーおよび SSRS)
  線や四角形を追加せずに、ヘッダー、フッター、およびレポート本文自体に罫線を追加することで、レポートに罫線を追加できます。  
  
 ページ ヘッダーとページ フッターに表示されるレポートの罫線を追加する場合は、レポートの最初と最後のページでヘッダーとフッターを非表示にしないでください。 非表示にした場合、レポートの最初と最後のページの上部または下部で罫線が一部しか表示されない可能性があります。 詳細については、「[ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a>レポートに罫線を追加するには  
  
1.  ヘッダー内のアイテムの外側で右クリックし、 **[ヘッダーのプロパティ]** をクリックします。 **[罫線]** タブで、左、上、右に、必要なスタイルを指定した罫線を追加します。  
  
    > [!NOTE]  
    >  レポートでヘッダーを使用しない、レポート本文、周囲に罫線を配置することができますかからヘッダーを追加する場合、**挿入**タブです。  
  
2.  デザイン画面のアイテムの外側の本文で右クリックし、 **[本文のプロパティ]** をクリックします。 **[罫線]** タブで、左および右に、必要なスタイルを指定した罫線を追加します。  
  
3.  フッター内のアイテムの外側で右クリックし、 **[フッターのプロパティ]** をクリックします。 **[罫線]** タブで、左、下、右に、必要なスタイルを指定した罫線を追加します。  
  
## <a name="see-also"></a>参照  
 [四角形と線&#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  