---
title: "PDW (Analytics Platform System) 用管理パックの SCOM のインポートします。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa735041-8e58-4886-ae3b-36f3c6298b12
caps.latest.revision: "6"
ms.openlocfilehash: 179395b7befdf934fcc44532944f4b535b9d3c5a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="import-the-scom-management-pack-for-pdw"></a>PDW の SCOM 管理パックをインポートします。
SQL Server PDW の System Center Operations Manager (SCOM) 管理パックをインポートする手順に従います。 管理パックは、SCOM から SQL Server PDW の監視に必要なです。  
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager 2007 R2 は、インストールして実行する必要があります。  
  
管理パックをインストールする必要があります。 参照してください[SCOM 管理パック &#40; をインストールAnalytics Platform System &#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>手順 1: SQL Server アプライアンス ベースの管理パックをインポートします。  
  
1.  Operations Manager 2007 管理グループの Operations Manager 管理者ロールのメンバーであるアカウントを使用して、コンピューターにログオンします。  
  
2.  オペレーション コンソールで **管理**です。  
  
3.  右クリックし、**管理パック**ノードをクリックして**管理パックのインポート**です。  
  
    ![[管理パックのインポート] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM_IMP")  
  
4.  管理パックの一覧で、[インポート] をクリックする管理パックを選択**選択**、クリックして**追加**です。  
  
    ![管理パック リスト](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  検索**アプライアンス**し、SQL Server アプライアンス ベースにドリルダウンし、をクリックし、**追加**2 つの選択肢です。  
  
    ![SQL Server アプライアンス ベース](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  2 つの管理パックは、下の選択したペインでが、一度クリックして**OK**です。  
  
    ![両方の管理パックを選択して](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  **[インストール]**をクリックします。  
  
    ![[インストール] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  完了すると、クリックして**閉じる**です。  
  
    ![完了すると、[閉じる] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Microsoft SQL Server 2008 R2 並列データ ウェアハウス アプライアンス用監視パックをインポートします。  
  
1.  右クリックし、**管理パック**ノードをクリックして**管理パックのインポート**です。  
  
2.  選択**ディスクから追加**しています.  
  
    ![管理パックを右クリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  SQL Server PDW 管理パックを展開した場所に移動し、「選択した管理パックをインポートする」セクションには、次の 3 つの管理パックを選択します。 最初の 1 つを選択し、shift キーを押しをクリックすると、最後の 1 つ選択して、これを行うことができます。 すべて選択すると、したら**開く**です。  
  
    ![管理パックの選択](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  **[インストール]**をクリックします。  
  
    ![[インストール] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  **[閉じる]**をクリックします。  
  
    ![[閉じる] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>次の手順  
管理パックをインポートしたら、これでは、次の手順に進む:[モニター Analytics Platform System &#40; を構成する SCOMAnalytics Platform System &#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
