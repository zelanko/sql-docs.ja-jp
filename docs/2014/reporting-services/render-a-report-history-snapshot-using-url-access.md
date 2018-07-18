---
title: URL アクセスを使用してレポート履歴スナップショットを表示する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b065fa70d102ff86c25aa0fffb78cfa4993cd284
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272578"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>URL アクセスを使用してレポート履歴スナップショットを表示する
  *rs:Snapshot* パラメーターを指定し、その値を有効なスナップショット ID に設定することによって、レポート履歴スナップショットに基づくレポートを表示できます。 パラメーターの値は、国際標準化機構 (ISO) 8601 の標準に基づく、YYYY-MM-DDTHH:MM:SS の形式です。  
  
 このパラメーターを省略した場合、レポートは、レポート サーバーのレポート実行およびキャッシュ管理オプションの設定に基づいて表示されます。 レポートの実行の詳細については、次を参照してください。[レポート処理プロパティの設定](report-server/set-report-processing-properties.md)します。  
  
## <a name="example"></a>例  
 次の例は、レポート履歴スナップショットを取得する URL を示します。  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>参照  
 [URL アクセス&#40;SSRS&#41;](url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
  
