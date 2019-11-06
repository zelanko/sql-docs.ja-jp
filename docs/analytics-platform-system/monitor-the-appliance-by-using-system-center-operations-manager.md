---
title: SCOM - Analytics Platform System での監視 |Microsoft Docs
description: System Center Operations Manager (SCOM) を使用すると、Analytics Platform System (APS) アプライアンスを監視できます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0da122b7ff4f17621a896e3a9f5076f8564d32c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960547"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>System Center Operations Manager - Analytics Platform System で監視します。
System Center Operations Manager (SCOM) を使用すると、Analytics Platform System (APS) アプライアンスを監視できます。
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>必須コンポーネント  
  
1.  System Center Operations Manager 2007 R2、2012、または 2012 SP1 は、インストールして実行する必要があります。  
  
2.  SQL Server 2008 R2 Native Client または SQL Server 2012 Native Client をインストールする必要があります。  
  
3.  SQL Server PDW を監視する管理パックのインストール、インポート、および構成する必要があります。 手順については、次の記事を使用すると、これらのタスクを実行できます。  
  
    -   [SCOM 管理パックをインストール&#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [PDW の SCOM 管理パックをインポート&#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Analytics Platform System を監視する SCOM 構成&#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>SQL Server PDW に SCOM を監視するには  
SCOM 管理パックを構成すると、SCOM の監視 ウィンドウをクリックし、下にドリル ダウン**SQL Server アプライアンス**し**Microsoft SQL Server 並列データ ウェアハウス**します。 Microsoft SQL Server 並列データ ウェアハウス、下には、4 つの選択肢があります。アラート、アプライアンス、アプライアンスの図、およびノード。  
  
### <a name="alerts"></a>オブジェクト エクスプローラーには  
アラートは、現在のアラートを管理するを見つけることができます。  
  
![アラート](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>アプライアンス  
アプライアンスは、環境内で現在検出および監視される SQL Server の PDW アプライアンスを表示します。 アプライアンスがここに表示しない ODBC 接続を作成した場合は、し、ある可能性があります、PDWWatcher アカウントに何らかの問題。 「監視しない」表示する場合がある、PDWMonitor アカウントに何らかの問題。 SCOM はリアルタイムで変更されることはありませんが、新しいアプライアンスを監視するを定期的にチェックするために辛抱強くし、アプライアンスを監視するためにクエリを定期的に送信します。  
  
![アプライアンス](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>アプライアンスの図  
アプライアンスの図のページは、ツリー ビューでは、アプライアンスの正常性確認を取得できます。  
  
![アプライアンスの図](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>ノード  
最後に、ノードのビューを使用すると、各ノードをアプライアンスの正常性を参照してください。  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Understanding 管理コンソールの警告&#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)  
  
