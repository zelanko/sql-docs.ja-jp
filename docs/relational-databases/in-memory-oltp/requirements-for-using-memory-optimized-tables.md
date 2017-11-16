---
title: "メモリ最適化テーブルを使用するための要件 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: 65
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d30c5b808c13258e784187182eab23b0a50c76e0
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="requirements-for-using-memory-optimized-tables"></a>メモリ最適化テーブルを使用するための要件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Azure DB でのインメモリ OLTP の使用については、「[SQL Database でのインメモリ (プレビュー) の使用](http://azure.microsoft.com/documentation/articles/sql-database-in-memory/)」を参照してください。  
  
 インメモリ OLTP を使用する場合、「 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」に加え、以下も要件です。  
  
-   SQL Server 2016 SP1 (以降) のあらゆるエディション。 SQL Server 2014 と SQL Server 2016 RTM (SP1 前) の場合、Enterprise、Developer、または Evaluation エディションが必要です。
    - 注: インメモリ OLTP には、64 ビット版の SQL Server が必要です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、メモリ最適化テーブルおよびインデックス内にデータを保持するために十分なメモリが必要です。また、オンライン ワークロードに対応するには、追加のメモリが必要です。 詳細については、「 [メモリ最適化テーブルのメモリ必要量の推定](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) 」を参照してください。  

-   仮想マシン (VM) で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行する場合、メモリ最適化テーブルとインデックスに必要なメモリに対応できるように、VM に十分なメモリを割り当てる必要があります。 VM ホスト アプリケーションによっては、VM のメモリ割り当てを保証する構成オプションはメモリ予約と呼ばれます。動的メモリを使用する場合は、最小 RAM と呼ばれます。 これらの設定が、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベースのニーズを十分に満たしていることを確認します。
  
-   持続性メモリ最適化テーブルの 2 倍のサイズの空きディスク領域。  
  
-   インメモリ OLTP を使用するための **cmpxchg16b** 命令をサポートするプロセッサ。 最新のすべての 64 ビット プロセッサでは **cmpxchg16b**がサポートされています。  
  
     仮想マシンを使用していて、古いプロセッサが原因のエラーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって表示される場合は、VM ホスト アプリケーションに **cmpxchg16b**を許可する構成オプションがあるかどうかをご確認ください。 該当する構成オプションがない場合は、Hyper-V を使用できます。Hyper-V では、構成オプションを変更することなく **cmpxchg16b** がサポートされています。  
  
-   インメモリ OLTP は **データベース エンジン サービス**の一部としてインストールされます。  
  
     レポートの生成 (「[テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)」) と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ( [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーでインメモリ OLTP を管理する場合) をインストールするには、 [SQL Server Management Studio (SSMS) をダウンロード](https://msdn.microsoft.com/library/mt238290.aspx)します。   
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>[!INCLUDE[hek_2](../../includes/hek-2-md.md)] の使用に関する重要な注意事項  
  
-   SQL Server 2016 を起動する際に、メモリ最適化テーブルのサイズには、空きメモリのサイズ以外の制限はありません。 SQL Server 2014 データベースの場合、データベース内の持続性のあるすべてのテーブルのメモリ内サイズの合計は、250 GB を超えないようにする必要があります。 詳細については、「 [メモリ最適化テーブルのメモリ必要量の推定](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)」を参照してください。  
    - 注: SQL Server 2016 SP1 より、Standard エディションと Express エディションではインメモリ OLTP がサポートされていますが、所与のデータベースでメモリ最適化テーブルに利用できるメモリ量にクォータが課せられます。 Standard エディションの場合、これはデータベースごとに 32GB です。Express エディションの場合、データベースごとに 352MB です。 
  
-   メモリ最適化テーブルが含まれるデータベースを 1 つ以上作成する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対してファイルの瞬時初期化を有効にする ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサービス開始アカウントに SE_MANAGE_VOLUME_NAME ユーザー権限を付与する) 必要があります。 ファイルの瞬時初期化を使用しない場合、メモリ最適化ストレージ ファイル (データ ファイルとデルタ ファイル) が作成時に初期化されるため、ワークロードのパフォーマンスが低下する場合があります。 ファイルの瞬時初期化に関する詳細については、「 [データベース ファイルの初期化](http://msdn.microsoft.com/library/ms175935\(SQL.105\).aspx)」をご覧ください。 ファイルの瞬時初期化を有効にする方法については、「 [How and Why to Enable Instant File Initialization (ファイルの瞬時初期化を有効にする方法と理由)](http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

