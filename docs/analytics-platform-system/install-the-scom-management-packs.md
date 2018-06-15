---
title: SCOM 管理パックの分析プラットフォーム システムをインストールする |Microsoft ドキュメント
description: 次の手順をダウンロードして SQL Server PDW の System Center Operations Manager (SCOM) 管理パックをインストールします。 管理パックは、SCOM から SQL Server PDW の監視に必要なです。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 163ab893074e171decb573d876c5f98334437985
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544684"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Analytics Platform System の SQL Server Operations Manager (SCOM) 管理パックをインストールします。
次の手順をダウンロードして SQL Server PDW の System Center Operations Manager (SCOM) 管理パックをインストールします。 管理パックは、SCOM から SQL Server PDW の監視に必要なです。  
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager は、インストールして実行する必要があります。 SQL Server PDW 2012 では、System Center Operations Manager 2007 R2、System Center Operations Manager 2012、または System Center Operations Manager 2012 service pack 1 が必要です。  
  
## <a name="Step1"></a>手順 1: 管理パックをダウンロードします。  
APS PDW ワークロードのダウンロード、 [Microsoft Analytics Platform System 用の System Center 管理パック](http://go.microsoft.com/fwlink/?LinkId=396857)です。  
  
アプライアンスの管理、ダウンロード、 [SQL Server アプライアンス ベースの管理パック](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=11436)です。  
  
以前のバージョンの PDW APS なしでは、ダウンロード、[用 Microsoft SQL Server 2012 並列データ ウェアハウス アプライアンスで、System Center 監視パック](http://go.microsoft.com/fwlink/p/?LinkId=282661)です。  
  
HDInsight のワークロード、ダウンロード、 [HDInsight 用 System Center 管理パック](http://go.microsoft.com/fwlink/?LinkId=390208)です。  
  
## <a name="Step2"></a>手順 2: 管理パックをインストールします。  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>SQL Server アプライアンス ベースの管理パックをインストールします。  
  
1.  インストールを実行するには、ダウンロードした SQL Server アプライアンス ベースの管理パックをダブルクリックします。  
  
2.  ライセンス契約に同意し、をクリックして**次**です。  
  
    ![ライセンス条項に同意](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  独自のインストール フォルダーを選択するか、既定の管理パックのインストール フォルダーを使用します。  
  
    ![インストール フォルダーの選択](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  **[インストール]** をクリックします。  
  
    ![インストールの確認](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  **[閉じる]** をクリックします。  
  
    ![[閉じる] をクリックして](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>SQL Server PDW アプライアンス用監視パックをインストールします。  
  
1.  インストールを実行するには、ダウンロードした SQL Server PDW アプライアンス管理パックをダブルクリックします。  
  
2.  ライセンス契約に同意し、をクリックして**次**です。  
  
    ![ライセンス agreeement を受け入れる](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  抽出したファイルを保持するディレクトリを選択します。 既定の管理パックのインストール フォルダーは、既定で表示されます。 既定値を選択するか、独自のインストール フォルダーを選択します。  
  
    ![インストール フォルダーの選択](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  **[インストール]** をクリックします。  
  
    ![インストールの確認](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  **[閉じる]** をクリックします。  
  
    ![インストールの完了](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>次の手順  
インストールされている管理パックがある場合は、これでは、次の手順に進む: [PDW 用 SCOM 管理パックのインポート&#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md)です。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
