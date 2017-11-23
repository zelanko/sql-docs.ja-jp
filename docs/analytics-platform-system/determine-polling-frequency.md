---
title: "ポーリング間隔 (Analytics Platform System) の決定します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062c0e3d-f7d0-44f1-aeab-a9bd17dc6fdd
caps.latest.revision: "7"
ms.openlocfilehash: fb32abc38a90cd7450dc310a9f73eb7a5d72b5fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="determine-polling-frequency"></a>ポーリングの頻度を決定します。
このトピックでは、SQL Server PDW アプライアンス通知のポーリング頻度を決定する方法について説明します。  
  
## <a name="to-determine-the-polling-frequency"></a>ポーリングの頻度を決定するには  
PDW サポートしていないので現在プロアクティブ通知アラートが発生したときに、監視ソリューションを継続的に、アプライアンスの Dll をポーリングする必要があります。  内部的には、PDW は、さまざまな間隔でコンポーネントをポーリングします。  
  
-   クラスター-60 秒  
  
-   ハートビート-60 秒  
  
-   他のすべてコンポーネント – 5 分  
  
-   – 3 秒のパフォーマンス カウンター  
  
System Center によっても使用される、共通のアラートをポーリングする間隔が**15 分ごと**です。  当然ながら、頻繁に増減したり、照会することが、6 時間未満であるごとにポーリングをお勧めできません。  
  
頻繁にポーリングが許容されるが、煩雑になります。 頻度が高すぎるポーリング、 [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/en-us/library/ms177648(v=sql11).aspx) DMV。  これは、ため、可能性の場合、クエリのパフォーマンス問題の診断にあるユーザーが簡単にクエリを実行ビューから外れてロールアップします。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンスの監視 &#40;です。Analytics Platform System &#41;](appliance-monitoring.md)  
  
