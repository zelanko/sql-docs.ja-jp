---
title: レポートをクリックスルー レポートとしてモデルにリンク |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 9dfe16933e0c2b335cf68816113c336561aac1ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175656"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>レポートをクリックスルー レポートとしてモデルにリンクする
  クリックスルー レポートの既定のテンプレートを使用する代わりに、レポート ビルダーのレポートを作成し、それをレポート モデルの特定のエンティティにリンクすることができます。 レポートを閲覧しているユーザーがメイン レポート内の対話型データをクリックすると、このレポートがクリックスルー レポートとして表示されます。 レポートをエンティティにリンクするには、次のように使用します。[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート マネージャー。  
  
> [!IMPORTANT]  
>  レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。  
  
### <a name="to-start-report-manager-from-a-browser"></a>ブラウザーからレポート マネージャーを起動するには  
  
1.  開いている[!INCLUDE[msCoName](../includes/msconame-md.md)]Internet Explorer 6.0 またはそれ以降。  
  
2.  Web ブラウザーのアドレス バーに、レポート マネージャーの URL を入力します。 既定では、URL は http://\<*ComputerName*>/reports です。  
  
### <a name="to-create-a-customized-clickthrough-report"></a>カスタマイズされたクリックスルー レポートを作成するには  
  
1.  カスタマイズされたクリックスルー レポートを追加するレポート モデルに移動します。  
  
2.  レポート モデルをダブルクリックします。  
  
3.  **[クリックスルー]** をクリックします。  
  
4.  カスタマイズされたクリックスルー レポートをアタッチするエンティティを選択します。  
  
    > [!NOTE]  
    >  このエンティティは、カスタマイズされたクリックスルー レポートの基本エンティティと同じものである必要があります。  
  
5.  選択したエンティティの単一のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、単一インスタンス レポートの **[参照]** ボタンをクリックします。  
  
     - または -  
  
     選択したエンティティの複数のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、複数インスタンス レポートの **[参照]** ボタンをクリックします。  
  
6.  レポートを選択し、 **[OK]** をクリックします。  
  
7.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [クリックスルー レポート&#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  