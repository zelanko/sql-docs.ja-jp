---
title: "インメモリ OLTP データベースにおける高可用性のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# インメモリ OLTP データベースにおける高可用性のサポート
  メモリ最適化テーブルを含んだデータベースは、ネイティブ コンパイル ストアド プロシージャの有無に関係なく、AlwaysOn 可用性グループで完全にサポートされます。  [!INCLUDE[hek_2](../../includes/hek-2-md.md)] オブジェクトを含んでいる場合とそうでない場合とでデータベースの構成とサポートに違いはありません。  
  
 インメモリ OLTP データベースが AlwaysOn 可用性グループ構成で配置されていると、再実行が行われたときに、プライマリ レプリカ上のメモリ最適化テーブルへの変更がメモリ内でセカンダリ レプリカ上のテーブルに適用されます。 つまり、データが既にメモリ内にあるため、セカンダリ レプリカへのフェールオーバーをすばやく実施できます。 これらのテーブルは、読み取りアクセス用に構成されたセカンダリ レプリカでのクエリにも利用できます。  
  
## AlwaysOn 可用性グループとインメモリ OLTP データベース  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] のコンポーネントを使ってデータベースを構成する利点を次に示します。  
  
-   **完全に統合された環境**   
    メモリ最適化テーブルを含んだデータベースは、同期と非同期のどちらのセカンダリ レプリカに対しても同じウィザードを使用して構成でき、同じサポート レベルが適用されます。 加えて、使い慣れた SQL Server Management Studio の AlwaysOn ダッシュボードを使用して、正常性の監視を行うことができます。  
  
-   **同等のフェールオーバー時間**   
    持続性のあるメモリ最適化テーブルのインメモリ状態がセカンダリ レプリカで維持されます。 自動フェールオーバーまたは強制フェールオーバーが発生した場合に復旧の必要がないため、新しいプライマリへのフェールオーバーにかかる時間はディスク ベースのテーブルと変わりありません。 この構成では、SCHEMA_ONLY として作成されたメモリ最適化テーブルがサポートされます。 ただしそれらのテーブルに対する変更はログに記録されないため、セカンダリ レプリカ上の該当テーブルにはデータが不在となります。  
  
-   **[読み取り可能セカンダリ]**   
    セカンダリ レプリカが読み取りアクセス用に構成されている場合、セカンダリ レプリカ上のメモリ最適化テーブルにアクセスしてクエリを実行することができます。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]では、セカンダリ レプリカ上の読み取りタイムスタンプは、プライマリ レプリカ上の読み取りタイムスタンプと同期に近い状態で保たれます。そのため、プライマリ レプリカへの変更はセカンダリに瞬時に反映されます。 この同期に近い動作は、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のインメモリ OLTP とは異なる点です。  
  
## フェールオーバー クラスタリング インスタンス (FCI) とインメモリ OLTP データベース  
 共有記憶域構成で高可用性を実現するには、メモリ最適化テーブルを含んだ 1 つ以上のデータベースを管理するインスタンスに対してフェールオーバー クラスタリングを設定します。 FCI を設定する際、次の要素を考慮する必要があります。  
  
-   **目標復旧時間**   
    フェールオーバーの所要時間は長くなる可能性があります。データベースを使用可能な状態にするためには、メモリ最適化テーブルをメモリに読み込む必要があるためです。  
  
-   **SCHEMA_ONLY テーブル**   
    フェールオーバー後、SCHEMA_ONLY テーブルは、データ行の存在しない空の状態になるので注意してください。 これは仕様であり、アプリケーションで定義された動作です。 1 つ以上の SCHEMA_ONLY テーブルを含む [!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースを再起動したときもまったく同じ動作となります。  
  
## インメモリ OLTP におけるトランザクション レプリケーションのサポート  
 トランザクション レプリケーションのサブスクライバーとして機能するテーブルは、ピア ツー ピア トランザクション レプリケーションを除き、メモリ最適化テーブルとして構成できます。 その他のレプリケーション構成はメモリ最適化テーブルとは互換性がありません。  詳細については、「[メモリ最適化テーブル サブスクライバーへのレプリケーション](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)」を参照してください。  
  
## 参照  
 [AlwaysOn 可用性グループ (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ (Always On 可用性グループ)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [メモリ最適化テーブル サブスクライバーへのレプリケーション](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)  
  
  