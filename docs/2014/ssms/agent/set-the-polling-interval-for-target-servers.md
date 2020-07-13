---
title: ターゲット サーバーのポーリング間隔の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067526"
---
# <a name="set-the-polling-interval-for-target-servers"></a>ターゲット サーバーのポーリング間隔の設定
  このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがマスターから対象サーバーに情報を更新する頻度を設定する方法について説明します。 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。 マルチサーバー ジョブとは、1 つ以上のターゲット サーバーでマスター サーバーにより実行されるジョブです。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **ターゲット サーバーのポーリング間隔を設定するために使用するもの:**  [SQL Server Management Studio](#SSMS)、[Transact-SQL](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
 各ターゲット サーバーは、同じジョブのインスタンスを同時に実行できます。 各ターゲット サーバーからマスター サーバーに定期的にポーリングし、そのターゲット サーバーに割り当てられた新しいジョブのコピーをダウンロードした後、切断します。 ダウンロードされたジョブはターゲット サーバーでローカルに実行され、マスター サーバーに再接続してジョブ結果状態をアップロードします。  
  
> [!NOTE]  
>  ターゲット サーバーがジョブの状態をアップロードするときにマスター サーバーにアクセスできない場合、そのジョブの状態はマスター サーバーがアクセスできるようになるまでスプールされます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) 」および「 [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)」を参照してください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
 **ターゲット サーバーのポーリング間隔を設定するには**  
  
1.  **オブジェクト エクスプローラー**で、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、**[マルチ サーバーの管理]** をポイントして、**[ターゲット サーバーの管理]** をクリックします。  
  
3.  **[ターゲット サーバーの状態]** タブで、**[命令を通知]** をクリックします。  
  
4.  **[命令の種類]** ボックスの一覧で、 **[ポーリング間隔の設定]** を選択します。  
  
5.  **[ポーリング間隔]** ボックスに、ターゲット サーバーがマスター サーバーをポーリングするまでの経過時間 (秒単位) を、10 から 28,800 までの範囲で入力します。  
  
6.  **[受信者]** で、次のいずれかの操作を行います。  
  
    1.  すべてのターゲット サーバーで同じポーリング間隔を共有する場合は、 **[すべてのターゲット サーバー]** をクリックします。  
  
    2.  すべてのターゲット サーバーで同じポーリング間隔を共有しない場合は、**[特定のターゲット サーバー]** をクリックし、このポーリング間隔を使用するターゲット サーバーを選択します。  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
 **ターゲット サーバーのポーリング間隔を設定するには**  
  
1.  オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリウィンドウで、 [sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)システムストアドプロシージャを使用して、対象サーバーのポーリング間隔を設定します。  
  
## <a name="see-also"></a>参照  
 [dbo.sysdownloadlist &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
