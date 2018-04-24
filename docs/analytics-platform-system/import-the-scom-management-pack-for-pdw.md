---
title: SCOM 管理パック - Analytics Platform System インポート |Microsoft ドキュメント
description: Analytics Platform System (APS) 用 System Center Operations Manager (SCOM) 管理パックをインポートする手順に従います。 SCOM から並列データ ウェアハウスを監視するには、管理パックが必要です。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e60d87ae58b0804a0a7296f8b489df7441683c5b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Analytics Platform System、SCOM 管理パックをインポートします。
Analytics Platform System (APS) 用 System Center Operations Manager (SCOM) 管理パックをインポートする手順に従います。 SCOM から並列データ ウェアハウスを監視するには、管理パックが必要です。 
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager 2007 R2 は、インストールして実行する必要があります。  
  
管理パックをインストールする必要があります。 参照してください[SCOM 管理パックをインストール&#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)です。  
  
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
管理パックをインポートしたら、これでは、次の手順に進む:[モニター分析プラットフォーム システムに構成する SCOM &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)です。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
