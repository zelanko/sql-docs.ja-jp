---
title: PDW サービスの状態 - Analytics Platform System |Microsoft ドキュメント
description: 並列データ ウェアハウス (PDW) サービスの分析プラットフォーム システムの状態。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e2252bb821f9522515f1625b0fc118323cb50d1f
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Analytics Platform System の並列データ ウェアハウス サービスの状態
Parallel Data Warehouse **Services ステータス** ページで、Microsoft Analytics Platform System Configuration Manager は、すべての SQL Server PDW サービスの状態を表示し、PDW サービスの開始し、停止に機能を提供します。 これは、のみサポートされているメソッドの開始と PDW サービスを停止します。 ある個々 のコンポーネントまたはサービスを開始できませんとは別に注意してください。  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>サービスを開始またはアプライアンスを停止するのには  
  
1.  アプライアンスのサービスを開始するには、クリックして**開始アプライアンス**です。  
  
2.  アプライアンスのサービスを停止する をクリックして**停止アプライアンス**です。  
  
をクリックする必要はありません**適用**して開始および停止アプライアンスのサービスを使用するときに**開始アプライアンス**と**アプライアンスの停止**です。  
  
![DWConfig アプライアンス PDW サービス](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> HDInsight リージョンのノードで、ディストリビューション エージェント (sqldwagent) PDW 領域を停止も停止します。 HDInsight リージョンが機能して、正常性の監視は使用できません。 (PDW エージェントに正常性の監視を報告する PDW 管理ノードが必要です)。  
  
## <a name="see-also"></a>参照  
[APS アプライアンスの電源をオンまたはオフ&#40;分析プラットフォーム システム&#41;](power-the-aps-appliance-on-or-off.md)  
  
