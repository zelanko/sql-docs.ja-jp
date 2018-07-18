---
title: サービスの状態 - Analytics Platform System の PDW |Microsoft Docs
description: Analytics Platform System の parallel Data Warehouse (PDW) のサービス状態。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6892bfcca05e0f85039dddee65a54b485a7ed433
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909892"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Analytics Platform System の parallel Data Warehouse サービスの状態
Parallel Data Warehouse**サービス状態**ページで Microsoft Analytics Platform System Configuration Manager が SQL Server PDW のすべてのサービスの現在の状態を表示しを停止および開始 PDW サービス機能を提供します。 これは、開始と停止 PDW サービスのみサポートされているメソッドです。 個々 のコンポーネントまたはサービスことはできませんとは独立してに起動することに注意してください。  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>サービスを開始またはアプライアンスを停止するのには  
  
1.  アプライアンスのサービスを開始するには、次のようにクリックします。**開始アプライアンス**します。  
  
2.  アプライアンスのサービスを停止するには、次のようにクリックします。**停止アプライアンス**します。  
  
クリックする必要はありません**適用**開始とを使用して、アプライアンスのサービスを停止するときに**開始アプライアンス**と**アプライアンスを停止**。  
  
![DWConfig アプライアンス PDW サービス](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> ノードで、ディストリビューション エージェント (sqldwagent) PDW リージョンの停止も停止します。 ディストリビューション エージェントには、正常性の監視を報告する PDW 管理ノードが必要です。  
  
## <a name="see-also"></a>参照  
[APS アプライアンスの電源オンまたはオフ&#40;Analytics Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  
