---
title: URL アクセスを使用してレポートを検索する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9ffac7320bc284547a8b5d0598c5523e5c0b09b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141704"
---
# <a name="search-a-report-using-url-access"></a>URL アクセスを使用してレポートを検索する
  URL アクセスを使用して、レポート内に特定の文字列があるかどうかを検索できます。 レポート内を検索するには、URL の *rc:FindString* パラメーターの値として検索する文字列を設定します。 さらに、 *rc:StartFind* パラメーターと *rc:EndFind* パラメーターを使用すれば、検索対象をレポート内の特定のページに絞り込むことができます。  
  
## <a name="example"></a>例  
 次の URL アクセスの例では、Product Catalog サンプル レポートの 1 ～ 5 ページを検索し、最初に出現する Mountain-400 という文字列を探します。  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>参照  
 [URL アクセス&#40;SSRS&#41;](url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
  
