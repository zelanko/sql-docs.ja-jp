---
title: Analytics Platform System の SCOM 管理パックのインポート |Microsoft Docs
description: Analytics Platform System (APS)、System Center Operations Manager (SCOM) 管理パックをインポートする次の手順に従います。 管理パックは、SCOM から Parallel Data Warehouse を監視する必要があります。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 070e7b73614f6884e45a5c91603d6086613d15ca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960859"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>SCOM 管理パックでは、Analytics Platform System をインポートします。
Analytics Platform System (APS)、System Center Operations Manager (SCOM) 管理パックをインポートする次の手順に従います。 管理パックは、SCOM から Parallel Data Warehouse を監視する必要があります。 
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager 2007 R2 は、インストールして実行する必要があります。  
  
管理パックをインストールする必要があります。 参照してください[SCOM 管理パックをインストール&#40;Analytics Platform System&#41;](install-the-scom-management-packs.md)します。  
  
## <a name="Step1"></a>手順 1:SQL Server アプライアンス ベースの管理パックをインポートします。  
  
1.  Operations Manager 2007 管理グループの Operations Manager 管理者ロールのメンバーであるアカウントを使用してコンピューターにログオンします。  
  
2.  オペレーション コンソールで、 **[管理]** をクリックします。  
  
3.  右クリックし、**管理パック**ノード、およびクリック**管理パックのインポート**します。  
  
    ![[管理パックのインポート] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM_IMP")  
  
4.  管理パックの一覧で、インポート をクリックする管理パックの選択**選択**、 をクリックし、**追加**。  
  
    ![管理パック リスト](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  検索**アプライアンス**と SQL Server のアプライアンスのベースにドリル ダウンし、クリックして**追加**2 つの選択肢です。  
  
    ![SQL Server アプライアンス ベース](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  下の選択したウィンドウに 2 つの管理パック後、クリックして**OK**します。  
  
    ![両方の管理パックを選択します](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4。")  
  
7.  **[インストール]** をクリックします。  
  
    ![[インストール] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  作業が完了したら**閉じる**します。  
  
    ![完了すると、[閉じる] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Microsoft SQL Server 2008 R2 並列データ ウェアハウス アプライアンスの監視パックをインポートします。  
  
1.  右クリックし、**管理パック**ノード、およびクリック**管理パックのインポート**します。  
  
2.  選択**ディスクから追加**.  
  
    ![管理パックを右クリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  SQL Server PDW 管理パックを展開した場所に移動し、「選択した管理パックをインポートする」セクションには、次の 3 つの管理パックを選択します。 1 つ目を選択し、shift キーを押しをクリックすると、最後の 1 つを選択すると、これを行うことができます。 すべて選択すると、クリックして**オープン**します。  
  
    ![管理パックの選択](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  **[インストール]** をクリックします。  
  
    ![[インストール] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  **[閉じる]** をクリックします。  
  
    ![[閉じる] をクリックして](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>次の手順  
これで、管理パックをインポートしたら、次の手順に進みます。[Analytics Platform System を監視する SCOM 構成&#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)します。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
