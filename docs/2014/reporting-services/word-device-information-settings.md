---
title: Word デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5b31b3c3ea0cf5b70967ca099e0b979f0c929334
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164001"
---
# <a name="word-device-information-settings"></a>Word デバイス情報設定
  次の表は、 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 形式で表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|`AutoFit`|`False`。 設定されている AutoFit `false` Word の表で設定します。<br /><br /> `True`。 設定されている AutoFit`true`すべて Word の表でします。<br /><br /> `Never`。 Word の表で AutoFit 値が設定されず、動作が Word の既定値に戻ります。<br /><br /> `Default`。 各論理ページごとに、物理的な描画領域 (余白を除いた物理ページの幅) よりも幅の狭い表で AutoFit が設定されます。|  
|`ExpandToggles`|表示と非表示の切り替えが可能なすべてのアイテムを完全に展開した状態で表示するかどうかを示します。 既定値は `false` です。|  
|`FixedPageWidth`|DOC ファイルに書き込まれるページの幅がレポート本文内で最大のページの幅に合わせて拡大されるかどうかを示します。 既定値は `false` です。|  
|**OmitHyperlinks**|ハイパーリンク アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。 既定値は `false`|  
|`OmitDrillthroughs`|ドリルスルー アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。 既定値は `false`|  
  
## <a name="see-also"></a>参照  
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  