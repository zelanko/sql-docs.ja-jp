---
title: "Oracle パブリッシングの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パブリッシング [SQL Server レプリケーション], Oracle パブリッシング"
  - "スナップショット レプリケーション [SQL Server], Oracle パブリッシング"
  - "Oracle パブリッシング [SQL Server レプリケーション]"
  - "トランザクション レプリケーション, Oracle パブリッシング"
  - "Oracle パブリッシング [SQL Server レプリケーション], Oracle パブリッシングについて"
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Oracle パブリッシングの概要
  始まる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], 、Oracle version 9i 以降、レプリケーション トポロジでは、Oracle パブリッシャーを含めることができます。 パブリッシング サーバーは、Oracle 対応の任意のハードウェアおよびオペレーティング システムに配置できます。 この機能は、既に確立されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスナップショット レプリケーションとトランザクション レプリケーションを基礎としており、同様のパフォーマンスと使い勝手が実現されています。  
  
 Oracle パブリッシングは推奨されません。 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## Oracle のスナップショット レプリケーション  
 Oracle のスナップショット パブリケーションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスナップショット パブリケーションと同じような方法で実装されます。 Oracle パブリケーションに対してスナップショット エージェントが実行されると、エージェントは Oracle パブリッシャーに接続し、パブリケーションの各テーブルを処理します。 各テーブルの処理では、テーブルの行が取得され、スキーマ スクリプトが作成されます。これらは、パブリケーションのスナップショット共有に格納されます。 スナップショット エージェントが実行されるたびにデータの完全なセットが作成されるため、Oracle テーブルにはトランザクション レプリケーションのように変更追跡のトリガーは追加されません。 スナップショット レプリケーションは、パブリッシング システムへの影響を最小限に抑えながらデータを移行するのに便利です。  
  
## Oracle のトランザクション レプリケーション  
 Oracle のトランザクション パブリケーションは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のトランザクション パブリッシング アーキテクチャを使用して実装されます。ただし、変更の追跡は、Oracle データベースのデータベース トリガーとログ リーダー エージェントの組み合わせによって行われます。 Oracle トランザクション パブリケーションのサブスクライバーは、スナップショット レプリケーションを使用して自動的に初期化されます。その後の変更はログ リーダー エージェントによって追跡され、変更が発生するとサブスクライバーに配信されます。  
  
 Oracle パブリケーションを作成すると、Oracle データベース内のパブリッシュされた各テーブルに対してトリガーと追跡テーブルが作成されます。 パブリッシュされたテーブルのデータが変更されると、テーブルのデータベース トリガーが起動されて、変更された各行の情報がレプリケーション追跡テーブルに挿入されます。 その後、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターのログ リーダー エージェントが、そのデータ変更情報を追跡テーブルからディストリビューターのディストリビューション データベースへと移動します。 最後に、標準のトランザクション レプリケーションと同じように、ディストリビューション エージェントが変更をディストリビューターからサブスクライバーに移動します。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの用語](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [異種データベース レプリケーション](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  