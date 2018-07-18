---
title: レポートをクリックスルー レポートとしてモデルにリンクする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3df0b140c8d1eb08fc3b1502eb2a627be7f175c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210732"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>レポートをクリックスルー レポートとしてモデルにリンクする
  クリックスルー レポートの既定のテンプレートを使用する代わりに、レポート ビルダーのレポートを作成し、それをレポート モデルの特定のエンティティにリンクすることができます。 レポートを閲覧しているユーザーがメイン レポート内の対話型データをクリックすると、このレポートがクリックスルー レポートとして表示されます。 レポートをエンティティにリンクする[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート マネージャー。  
  
> [!IMPORTANT]  
>  レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。  
  
### <a name="to-start-report-manager-from-a-browser"></a>ブラウザーからレポート マネージャーを起動するには  
  
1.  開いている[!INCLUDE[msCoName](../includes/msconame-md.md)]Internet Explorer 6.0 以降。  
  
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
  
  
