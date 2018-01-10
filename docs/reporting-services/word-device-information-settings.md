---
title: "Word デバイス情報設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b6ca29c16e7b50183623530f8bceedd349c1f23f
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="word-device-information-settings"></a>Word デバイス情報設定
  次の表は、 [!INCLUDE[ofprword](../includes/ofprword-md.md)] 形式で表示するためのデバイス情報設定を示しています。  
  
|設定|ReplTest1|  
|-------------|-----------|  
|**AutoFit**|**[False]**。 Word のすべての表で AutoFit が **false** に設定されます。<br /><br /> **[True]**。 Word のすべての表で AutoFit が **true** に設定されます。<br /><br /> **Never**。 Word の表で AutoFit 値が設定されず、動作が Word の既定値に戻ります。<br /><br /> **Default**。 各論理ページごとに、物理的な描画領域 (余白を除いた物理ページの幅) よりも幅の狭い表で AutoFit が設定されます。|  
|**ExpandToggles**|表示と非表示の切り替えが可能なすべてのアイテムを完全に展開した状態で表示するかどうかを示します。 既定値は **false**です。|  
|**FixedPageWidth**|DOC ファイルに書き込まれるページの幅がレポート本文内で最大のページの幅に合わせて拡大されるかどうかを示します。 既定値は **false**です。|  
|**OmitHyperlinks**|ハイパーリンク アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。 既定値は **false**です。|  
|**OmitDrillthroughs**|ドリルスルー アクションが設定されているすべてのアイテムでそのアクションを省略するかどうかを示します。 既定値は **false**です。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
