---
title: SCOM - Analytics Platform System とモニター |Microsoft ドキュメント
description: System Center Operations Manager (SCOM) を使用すると、Analytics Platform System (APS) アプライアンスを監視できます。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c2b26462ab37cf7d63960ff7db6e20c57e8290bb
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>System Center Operations Manager の Analytics Platform System とモニター
System Center Operations Manager (SCOM) を使用すると、Analytics Platform System (APS) アプライアンスを監視できます。
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
  
1.  System Center Operations Manager 2007 R2、2012、または 2012 SP1 は、インストールして実行する必要があります。  
  
2.  SQL Server 2008 R2 Native Client または SQL Server 2012 Native Client をインストールする必要があります。  
  
3.  SQL Server PDW と HDInsight を監視する管理パックのインストール、インポート、および構成されている必要があります。 手順については、次の記事を使用すると、これらのタスクを実行できます。  
  
    -   [SCOM 管理パックをインストール&#40;分析プラットフォーム システム&#41;](install-the-scom-management-packs.md)  
  
    -   [PDW の SCOM 管理パックをインポート&#40;分析プラットフォーム システム&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [構成を分析プラットフォーム システムを監視する SCOM&#40;分析プラットフォーム システム&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>SQL Server PDW SCOM とを監視するには  
SCOM 管理パックを構成した後の監視 ウィンドウの SCOM をクリックし、ドリルダウン**SQL Server アプライアンス**し**Microsoft SQL Server 並列データ ウェアハウス**です。 Microsoft SQL Server 並列データ ウェアハウスの下には、次の 4 つの選択肢があります: アラート、アプライアンス、アプライアンスの図、およびノード。  
  
### <a name="alerts"></a>警告  
アラートは、管理する現在のアラートを見つけることができます。  
  
![アラート](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>アプライアンス  
アプライアンスは、環境内で現在検出され、監視している SQL Server の PDW アプライアンスを表示します。 アプライアンスが表示されないここでの ODBC 接続を作成した場合、し、ある可能性があります、PDWWatcher アカウントに何らかの問題です。 「監視しない」表示する場合があります、PDWMonitor アカウントに何らかの問題。 SCOM がリアルタイムで変更されることはできませんが、定期的に監視する新しいアプライアンスのチェックのために、患者をでし、定期的にアプライアンスを監視するためにクエリを送信します。  
  
![アプライアンス](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>アプライアンスの図  
アプライアンスの図のページは、ツリー ビューでは、アプライアンスの正常性を見てを取得できます。  
  
![アプライアンスの図](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>ノード  
最後に、ノードのビューには、各ノードをアプライアンスのヘルスを表示することができます。  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Understanding 管理コンソールの警告&#40;分析プラットフォーム システム&#41;](understanding-admin-console-alerts.md)  
  
