---
title: System Center Operations Manager (AP) とモニター アプライアンス
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de6cbf6e-f2e9-4877-94df-9c13b1182d56
caps.latest.revision: 14
ms.openlocfilehash: 02bdd22c66729ab471298e211b619e1cb1e4565c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="monitor-the-appliance-by-using-system-center-operations-manager"></a>System Center Operations Manager を使用してアプライアンスを監視します。
これには、System Center Operations Manager を使用して、SQL Server PDW と HDInsight を監視する方法について説明します。  
  
## <a name="before-you-begin"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
  
1.  System Center Operations Manager 2007 R2、2012、または 2012 SP1 は、インストールして実行する必要があります。  
  
2.  SQL Server 2008 R2 Native Client または SQL Server 2012 Native Client をインストールする必要があります。  
  
3.  SQL Server PDW と HDInsight を監視する管理パックのインストール、インポート、および構成されている必要があります。 手順については、次を使用すると、これらのタスクを実行できます。  
  
    -   [SCOM 管理パックをインストール&#40;分析プラットフォーム システム&#41;](install-the-scom-management-packs.md)  
  
    -   [PDW の SCOM 管理パックをインポート&#40;分析プラットフォーム システム&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [構成を分析プラットフォーム システムを監視する SCOM&#40;分析プラットフォーム システム&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>SQL Server PDW SCOM とを監視するには  
SCOM 管理パックを構成した後の監視 ウィンドウの SCOM をクリックし、ドリルダウン**SQL Server アプライアンス**し**Microsoft SQL Server 並列データ ウェアハウス**です。 Microsoft SQL Server 並列データ ウェアハウスの下には、次の 4 つの選択肢があります: アラート、アプライアンス、アプライアンスの図、およびノード。  
  
### <a name="alerts"></a>警告  
アラートは、管理する現在のアラートを見つけることができます。  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>アプライアンス  
アプライアンスは、環境内で現在検出され、監視している SQL Server の PDW アプライアンスを表示します。 アプライアンスが表示されないここでの ODBC 接続を作成した場合、し、ある可能性があります、PDWWatcher アカウントに何らかの問題です。 「監視しない」として表示する場合があります、PDWMonitor アカウント何らかの問題。 のでお待ち SCOM がリアルタイムで変更されることはできませんが、定期的に監視する新しいアプライアンスのチェックし、定期的に監視するためのアプライアンスにクエリを送信します。  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>アプライアンスの図  
アプライアンスの図のページは、ツリー ビューでは、アプライアンスの正常性を見てを取得できます。  
  
![アプライアンスの図](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>ノード  
最後に、ノードのビューには、各ノードをアプライアンスのヘルスを表示することができます。  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Understanding 管理コンソールの警告&#40;分析プラットフォーム システム&#41;](understanding-admin-console-alerts.md)  
  
