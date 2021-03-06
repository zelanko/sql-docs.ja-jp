---
title: データベース ミラーリング セッションの手動フェールオーバー (SQL Server Management Studio) | Microsoft Docs
description: SQL Server Management Studio を使用して、ミラー サーバーへの手動フェールオーバーを開始する方法について説明します。 その後は、ミラー データベースがプリンシパル データベースになります。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 05e11b27e618dfc38f818f8dc86199cce3343d21
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754634"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a>データベース ミラーリング セッションの手動フェールオーバー (SQL Server Management Studio)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  ミラー化されたデータベースが同期されている場合 (つまり、データベースが SYNCHRONIZED 状態である場合)、データベース所有者はミラー サーバーに対して手動フェールオーバーを開始できます。  
  
 手動フェールオーバー中、フェールオーバーが発生するデータベースに対するプリンシパル サーバーとミラー サーバーのロールが切り替わります。 その結果、ミラー データベースがプリンシパル データベースになり、プリンシパル データベースがミラー データベースになります。 次の表は、 `SQLDBENGINE0_1` と `SQLDBENGINE0_2`という 2 つのミラーリング パートナーを例にとって、そのロールが手動フェールオーバーによってどのように切り替わるかを示しています。  
  
|サーバー|フェールオーバー前|フェールオーバー後|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|PRINCIPAL|MIRROR|  
|`SQLDBENGINE0_2`|MIRROR|PRINCIPAL|  
  
 その他のデータベース ミラーリング セッションに対するサーバーのロールは影響を受けません。 詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。  
  
### <a name="to-manually-fail-over-database-mirroring"></a>データベース ミラーリングを手動でフェールオーバーするには  
  
1.  プリンシパル サーバー インスタンスに接続し、 **[オブジェクト エクスプローラー]** ペインでサーバー名をクリックして、サーバー ツリーを展開します。  
  
2.  **[データベース]** を展開し、フェールオーバー先のデータベースをクリックします。  
  
3.  データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。  
  
4.  **[フェールオーバー]** をクリックします。  
  
     確認のメッセージが表示されます。  Windows 認証を使用してミラー サーバーに接続しようとすると、プリンシパル サーバーが開始されます。 Windows 認証が機能しない場合は、プリンシパル サーバーに **[サーバーへの接続]** ダイアログ ボックスが表示されます。 ミラー サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、 **[認証]** ボックスで **[SQL Server 認証]** を選択します。 **[ログイン]** テキスト ボックスで、ミラー サーバー上で接続するログイン アカウントを指定し、 **[パスワード]** テキスト ボックスで、そのアカウントのパスワードを指定します。  
  
     フェールオーバーに成功すると、 **[データベースのプロパティ]** ダイアログ ボックスが閉じます。 その結果、ミラー データベースがプリンシパル データベースになり、プリンシパル データベースがミラー データベースになります。  
  
     フェールオーバーに失敗すると、エラー メッセージが表示され、ダイアログ ボックスが開いたままになります。  
  
    > [!IMPORTANT]  
    >  **[ミラーリング]** ページを開いた後でプロパティを変更した場合、それらの変更内容は保存されません。  
  
     ダイアログ ボックスが自動的に閉じられます。  
  
## <a name="see-also"></a>参照  
 [データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリング セッションを手動でフェールオーバーする &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)   
 [データベース ミラーリング セッションを一時停止または再開する &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [データベース ミラーリングを削除する &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
  
