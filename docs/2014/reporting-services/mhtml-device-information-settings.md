---
title: MHTML デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: dd75a21625eb3ab31c9b1655e0f85943470cee54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117470"
---
# <a name="mhtml-device-information-settings"></a>MHTML デバイス情報設定
  次の表は、Web アーカイブ (MHTML) 形式でレポートを表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**JavaScript**|表示レポートで JavaScript がサポートされるかどうかを示します。|  
|**OutlookCompat**|Outlook でレポートの外観をよくする追加のメタデータを使用して表示するかどうかを示します。 既定値は `true` です。|  
|**MHTML Fragment**|完全な MHTML ドキュメントの代わりに MHTML を断片として作成するかどうかを示します。 MHTML の断片には、TABLE 要素のレポート コンテンツが含まれ、HTML 要素と BODY 要素が省略されます。 既定値は `false` です。|  
|**DataVisualizationFitSizing**|Tablix 内でのデータの視覚エフェクトの調整動作を示します。 これには、グラフ、ゲージ、およびマップが含まれます。<br /><br /> 有効な値は、 **Approximate** および **Exact**です。<br /><br /> 既定値は **Approximate**です。 この設定を **rsreportserver.config** ファイルから削除すると、既定の動作は **Exact**になります。<br /><br /> **Exact** を有効にした場合は、正確なサイズを特定する処理に時間がかかることがあるため、パフォーマンスに影響する可能性があります。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
