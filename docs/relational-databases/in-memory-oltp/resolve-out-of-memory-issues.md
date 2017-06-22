---
title: "メモリ不足の問題の解決 | Microsoft Docs"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d6eef790f729a3270c0ba046d6a60114ae2da8dc
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="resolve-out-of-memory-issues"></a>メモリ不足の問題の解決
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] では、さまざまな形で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より多くのメモリが使用されます。 インストールして [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 用に割り当てたメモリ量が、ニーズの拡大に合わなくなる場合があります。 その場合は、メモリが不足する可能性があります。 このトピックでは、OOM 状態から回復する方法について説明します。 多数の OOM 状態を回避するのに役立つガイドについては、「 [メモリ使用量の監視とトラブルシューティング](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md) 」を参照してください。  
  
## <a name="covered-in-this-topic"></a>このトピックの内容  
  
|トピック|概要|  
|-----------|--------------|  
|[OOM によるデータベース復元の障害を解決する](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_resolveRecoveryFailures)|"リソース プール '*\<resourcePoolName>*' 内のメモリ不足が原因で、データベース '*\<databaseName>*' の復元操作に失敗しました" というエラー メッセージが表示された場合の対処方法。|  
|[低メモリまたは OOM 状態によるワークロードへの影響を解決する](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_recoverFromOOM)|低メモリの問題によるパフォーマンス低下が見つかった場合の対処方法。|  
|[十分なメモリがある状況でのメモリ不足によるページの割り当てエラーを解決する](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_PageAllocFailure)|操作に十分なメモリがあるにもかかわらず、"リソース プール '*\<resourcePoolName>*' のメモリが不足しているため、データベース '*\<databaseName>*' のページ割り当ては禁止されています。 …" というエラー メッセージが発生した場合の対処方法。|  
  
##  <a name="bkmk_resolveRecoveryFailures"></a> OOM によるデータベース復元の障害を解決する  
 データベースを復元しようとすると、"リソース プール '*\<resourcePoolName>*' 内のメモリ不足が原因で、データベース '*\<databaseName>*' の復元操作に失敗しました" というエラー メッセージが表示されることがあります。これは、データベースを復元するのに十分なメモリがサーバーにないことを示します。
   
データベースの復元先であるサーバーでは、データベース バックアップのメモリ最適化テーブル用に十分なメモリが確保されている必要があります。メモリが十分でない場合、データベースはオンラインになりません。  
  
サーバーは十分な物理メモリを備えているのに、このエラーが引き続き発生する場合は、他のプロセスで大量のメモリを使用されているか、または構成上の問題で復元用に十分なメモリが確保されていないことが考えられます。 この種の問題については、次の対策を実施して、復元操作でより多くのメモリを使用できるようにします。 
  
-   実行中のアプリケーションを一時的に閉じます。   
    実行中のアプリケーションを 1 つ以上閉じるか、または現時点で必要のないサービスを停止することにより、それらのアプリケーションまたはサービスで使用されていたメモリを復元操作で使用できるようにします。 閉じたアプリケーションは、復元操作の正常完了後に再起動できます。  
  
-   MAX_MEMORY_PERCENT の値を増やします。   
    データベースが [リソース プールにバインドされている](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)場合 (ベスト プラクティス)、復元で使用できるメモリは MAX_MEMORY_PERCENT によって管理されます。 値が小さすぎると、復元は失敗します。 このコード スニペットでは、リソース プール PoolHk の MAX_MEMORY_PERCENT を変更して、インストールされているメモリの 70% に設定します。  
  
    > [!IMPORTANT]  
    >  サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT を MAX_MEMORY_PERCENT と同じ値に設定してください。   
    > 詳細については、「 [ベスト プラクティス: VM 環境でのインメモリ OLTP の使用](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) 」をご覧ください。  
  
    ```tsql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     MAX_MEMORY_PERCENT の最大値については、「 [メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable)」をご覧ください。  
  
-   **max server memory**の値を大きくします。  
    **max server memory** の構成については、「 [メモリ構成オプションを使用したサーバー パフォーマンスの最適化](http://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx)」をご覧ください。  
  
##  <a name="bkmk_recoverFromOOM"></a> 低メモリまたは OOM 状態によるワークロードへの影響を解決する  
 言うまでもなく、低メモリまたは OOM (メモリ不足) の状態にならないことがベストです。 適切なプラン作成と監視によって、OOM 状態を回避することができます。 ただし、最適なプランを作成しても、実際に起こることを予測できるとは限らず、結果として低メモリまたは OOM の状態になる場合もあります。 OOM からの復旧には、次の 2 段階があります。  
  
1.  [DAC (専用管理者接続) を開く](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_openDAC)  
  
2.  [修正措置を行う](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_takeCorrectiveAction)  
  
###  <a name="bkmk_openDAC"></a> DAC (専用管理者接続) を開く  
 Microsoft SQL Server は、専用管理者接続 (DAC) を提供します。 DAC を使用すると、サーバーが他のクライアント接続に応答しない場合でも、SQL Server データベース エンジンの実行中のインスタンスにアクセスして、サーバーの問題をトラブルシューティングすることができます。 DAC は、 `sqlcmd` ユーティリティおよび SQL Server Management Studio (SSMS) を介して利用できます。  
  
 `sqlcmd` および DAC の使用方法については、「 [専用管理者接続の使用](http://msdn.microsoft.com/library/ms189595\(v=sql.100\).aspx/css)」をご覧ください。 SSMS を介して DAC を使用する方法については、「 [SQL Server Management Studio で専用管理者接続を使用する方法](http://msdn.microsoft.com/library/ms178068.aspx)」をご覧ください。  
  
###  <a name="bkmk_takeCorrectiveAction"></a> 修正措置を行う  
 OOM 状態を解決するには、使用率を削減して既存メモリを解放するか、インメモリ テーブルに使用できるメモリ量を増やす必要があります。  
  
#### <a name="free-up-existing-memory"></a>既存メモリを解放する  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>メモリ最適化テーブルの不要な行を削除し、ガベージ コレクションを待機する  
 メモリ最適化テーブルから、不要な行を削除できます。 ガベージ コレクターによって、これらの行で使用されていたメモリが使用可能メモリに返されます。 より多くのメモリが使用されます。 インメモリ OLTP エンジンは、ガベージ行を積極的に回収します。 ただし、実行時間が長いトランザクションではガベージ コレクションが行われないことがあります。 たとえば、5 分間実行されているトランザクションの場合、トランザクションがアクティブな状態で更新操作または削除操作によって作成された行バージョンは、ガベージ コレクションで回収することができません。  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>1 つ以上の行をディスク ベース テーブルに移動する  
 TechNet の次の資料では、メモリ最適化テーブルからディスク ベース テーブルに行を移動する方法について説明しています。  
  
-   [アプリケーション レベルのパーティション分割](http://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン](http://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>使用可能なメモリを増やす  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>リソース プールの MAX_MEMORY_PERCENT 値を増やす  
 インメモリ テーブル用に名前付きリソース プールを作成していない場合は、作成して [!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースをバインドします。 [データベースを作成してリソース プールにバインドする方法については、「](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) メモリ最適化テーブルを持つデータベースのリソース プールへのバインド [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 」を参照してください。  
  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースがリソース プールにバインドされている場合は、プールがアクセスできるメモリのパーセントを増やせることがあります。 リソース プールの MIN_MEMORY_PERCENT および MAX_MEMORY_PERCENT の値を変更する方法については、サブトピック「 [既存のプール内での MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の変更](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation) 」をご覧ください。  
  
 MAX_MEMORY_PERCENT の値を増やします。   
このコード スニペットでは、リソース プール PoolHk の MAX_MEMORY_PERCENT を変更して、インストールされているメモリの 70% に設定します。  
  
> [!IMPORTANT]  
>  サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT を同じ値に設定してください。   
> 詳細については、「 [ベスト プラクティス: VM 環境でのインメモリ OLTP の使用](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) 」をご覧ください。  
  
```tsql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 MAX_MEMORY_PERCENT の最大値については、「 [メモリ最適化テーブルおよびインデックスで使用可能なメモリの割合](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable)」をご覧ください。  
  
##### <a name="install-additional-memory"></a>追加メモリをインストールする  
 可能であれば、最終的に最上のソリューションは、追加の物理メモリをインストールすることです。 その場合は、 [でそれ以上のメモリが必要である可能性は低いため、新しくインストールされたメモリのすべてがリソース プールで使用可能でない場合はそれを活用して、MAX_MEMORY_PERCENT 値 (サブトピック「](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation)既存のプール内での MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT の変更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照) も増やせる可能性があります。  
  
> [!IMPORTANT]  
>  サーバーが VM 上で実行されており、専用用途ではない場合は、MIN_MEMORY_PERCENT と MAX_MEMORY_PERCENT を同じ値に設定してください。   
> 詳細については、「 [ベスト プラクティス: VM 環境でのインメモリ OLTP の使用](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) 」をご覧ください。  
  
##  <a name="bkmk_PageAllocFailure"></a> 十分なメモリがある状況でのメモリ不足によるページの割り当てエラーを解決する  
 ページを割り当てるだけの十分な物理メモリがあるにもかかわらず、"リソース プール '*\<resourcePoolName>*' のメモリが不足しているため、データベース '*\<databaseName>*' のページ割り当ては禁止されています。 詳細については、'http://go.microsoft.com/fwlink/?LinkId=330673' をご覧ください。" というエラー メッセージが エラー ログに記録される場合は、原因として、リソース ガバナーが無効になっている可能性があります。 リソース ガバナーが無効になっていると、MEMORYBROKER_FOR_RESERVE によって擬似的なメモリ不足が引き起こされます。  
  
 これを解決するには、リソース ガバナーを有効にする必要があります。  
  
 オブジェクト エクスプローラー、リソース ガバナーのプロパティ、または Transact-SQL を使用してリソース ガバナーを有効にする方法や、制限事項と制約事項については、「 [リソース ガバナーの有効化](http://technet.microsoft.com/library/bb895149.aspx) 」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP のメモリ管理](http://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)   
 [メモリ使用量の監視とトラブルシューティング](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)   
 [データベースを作成してリソース プールにバインドする方法については、「](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [ベスト プラクティス: VM 環境でのインメモリ OLTP の使用](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9)  
  
  

