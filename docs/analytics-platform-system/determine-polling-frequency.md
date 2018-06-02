---
title: ポーリング頻度 - Analytics Platform System |Microsoft ドキュメント
description: この記事では、Analytics Platform System アプライアンス通知のポーリング頻度を決定する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 39597e0e4623a3006709acde7fe54f97545c362f
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707620"
---
# <a name="determine-polling-frequency"></a>ポーリングの頻度を決定します。
この記事では、Analytics Platform System アプライアンス通知のポーリング頻度を決定する方法について説明します。  
  
## <a name="to-determine-the-polling-frequency"></a>ポーリングの頻度を決定するには  
PDW サポートしていないので現在プロアクティブ通知アラートが発生したときに、監視ソリューションを継続的に、アプライアンスの Dll をポーリングする必要があります。  内部的には、PDW は、さまざまな間隔でコンポーネントをポーリングします。  
  
-   クラスター-60 秒  
  
-   ハートビート-60 秒  
  
-   他のすべてコンポーネント – 5 分  
  
-   – 3 秒のパフォーマンス カウンター  
  
System Center によっても使用される、共通のアラートをポーリングする間隔が**15 分ごと**です。  当然ながら、頻繁に増減したり、照会することが、6 時間未満であるごとにポーリングをお勧めできません。  
  
頻繁にポーリングが許容されるが、煩雑になります。 頻度が高すぎるポーリング、 [sys.dm_pdw_nodes_exec_requests](http://msdn.microsoft.com/library/ms177648(v=sql11).aspx) DMV。  ポーリングの頻度が高すぎるため、可能性が困難なクエリのパフォーマンスを診断するユーザーに対して発行するときに、ビューから外れて迅速にロールバックします。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンス監視&#40;分析プラットフォーム システム&#41;](appliance-monitoring.md)  
  
