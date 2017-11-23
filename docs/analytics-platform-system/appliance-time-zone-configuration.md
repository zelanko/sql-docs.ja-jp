---
title: "アプライアンスのタイム ゾーンの構成 (Analytics Platform System)"
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
ms.assetid: cea9eeb9-fe05-4e65-b229-539de02ab20a
caps.latest.revision: "18"
ms.openlocfilehash: 05cf2811dad14a6a7d53752893f363b061b86843
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="appliance-time-zone-configuration"></a>アプライアンスのタイム ゾーンの構成
**タイム ゾーン** ページでは、SQL Server PDW アプライアンス上のすべてのノードのタイム ゾーンを設定することができます。  
  
## <a name="to-set-the-time-zone"></a>タイム ゾーンを設定するには  
  
1.  構成マネージャーを起動します。 詳細については、次を参照してください[構成マネージャー &#40; を起動。Analytics Platform System &#41;](launch-the-configuration-manager.md).  
  
2.  使用してアプライアンスのサービスを停止、 **Services ステータス**Configuration Manager でのページです。 参照してください[PDW サービスの状態と #40 です。Analytics Platform System &#41;](pdw-services-status.md)手順についてはします。  
  
3.  構成マネージャーの左側のウィンドウでをクリックして**タイム ゾーン**です。 必要なタイム ゾーンを選択、**タイム ゾーン**ドロップ ダウン メニュー。 場所に応じてこともできます横のボックスをオンに**夏時間の時計を自動的に調整**です。  
  
4.  をクリックして**適用**して変更を保存します。  
  
5.  使用して、アプライアンスのサービスを再起動して、 **Services ステータス**Configuration Manager でのページです。 また、計画している、権限を変更する場合は、アプライアンスを再開する前に行うをことができます。  
  
![DWConfig アプライアンスの時刻](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>参照  
[構成マネージャー &#40; を起動します。Analytics Platform System &#41;](launch-the-configuration-manager.md)  
  
