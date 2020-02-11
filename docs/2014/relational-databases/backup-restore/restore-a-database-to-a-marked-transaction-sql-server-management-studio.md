---
title: マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 919c10372e397f0c2d66d7648363aef7916ec598
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875601"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a>マークされたトランザクションへのデータベースの復元 (SQL Server Management Studio)
  データベースが復元中の状態にある場合、[**トランザクションログの復元**] ダイアログボックスを使用して、使用可能なログバックアップ内のマークされたトランザクションにデータベースを復元できます。  
  
> [!NOTE]  
>  詳細については、「[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル#41;](use-marked-transactions-to-recover-related-databases-consistently.md)」および「[マークされたトランザクションを含む関連データベースの復旧](recovery-of-related-databases-that-contain-marked-transaction.md)」を参照してください。  
  
### <a name="to-restore-a-marked-transaction"></a>マークされたトランザクションを復元するには  
  
1.  の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]適切なインスタンスに接続した後、オブジェクトエクスプローラーで、サーバー名をクリックしてサーバーツリーを展開します。  
  
2.  [**データベース] を展開し**、データベースに応じて、ユーザーデータベースを選択するか、[**システムデータベース**] を展開してシステムデータベースを選択します。  
  
3.  データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。  
  
4.  
  **[トランザクション ログ]** をクリックして **[トランザクション ログの復元]** ダイアログ ボックスを開きます。  
  
5.  
  **[全般]** ページの **[復元先]** で、 **[マークされたトランザクション]** をクリックします。 **[マークされたトランザクションの選択]** ダイアログ ボックスが開きます。 このダイアログ ボックスには、選択したトランザクション ログ バックアップで使用できるマークされたトランザクションを一覧表示するグリッドが表示されます。  
  
     既定では、マークされたトランザクションの前まで復元され、マークされたトランザクションは復元されません。 マークされたトランザクションも復元するには、 **[マークされたトランザクションを含める]** チェック ボックスをオンにします。  
  
     次の表は、グリッドの列ヘッダーとその値を示しています。  
  
    |ヘッダー|Value|  
    |------------|-----------|  
    |\<空白の>|マークを選択するためのチェック ボックスを表示します。|  
    |**トランザクションマーク**|トランザクションがコミットされたときにユーザーによって指定された、マークされたトランザクションの名前。|  
    |**予定**|トランザクションがコミットされた日時。 トランザクションの日付と時刻は、クライアント コンピューターの日付と時刻ではなく、 **msdbgmarkhistory** テーブルに記録されたとおりに表示されます。|  
    |**説明**|トランザクションがコミットされたときにユーザーが指定したマークされたトランザクションの説明 (該当する場合)。|  
    |**LSN**|マークされたトランザクションのログ シーケンス番号。|  
    |**[データベース]**|マークされたトランザクションがコミットされたデータベースの名前。|  
    |**ユーザー名**|マークされたトランザクションをコミットしたデータベース ユーザーの名前。|  
  
## <a name="see-also"></a>参照  
 [データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [トランザクションログバックアップを復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
  
