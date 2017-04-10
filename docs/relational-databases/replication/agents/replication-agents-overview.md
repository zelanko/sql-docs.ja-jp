---
title: "レプリケーション エージェントの概要 | Microsoft Docs"
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
  - "ディストリビューション エージェント"
  - "エージェント [SQL Server レプリケーション]"
  - "キュー リーダー エージェント, キュー リーダー エージェントについて"
  - "キュー リーダー エージェント (Queue Reader Agent)"
  - "マージ エージェント, マージ エージェントについて"
  - "ログ リーダー エージェント, ログ リーダー エージェントについて"
  - "レプリケーション [SQL Server], エージェントおよびプロファイル"
  - "ログ リーダー エージェント (Log Reader Agent)"
  - "ディストリビューション エージェント, ディストリビューション エージェントについて"
  - "エージェント [SQL Server レプリケーション], エージェントについて"
  - "マージ エージェント"
  - "スナップショット エージェント, スナップショット エージェントについて"
  - "スナップショット エージェント"
ms.assetid: a35ecd7d-f130-483c-87e3-ddc8927bb91b
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# レプリケーション エージェントの概要
  レプリケーションでは、エージェントと呼ばれる多数のスタンドアロン プログラムを使用して、変更の監視やデータの配信に関連するタスクを実行します。 既定では、レプリケーション エージェントは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントでスケジュールされたジョブとして実行されるため、ジョブを実行するためには [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントが実行中であることが必要です。 レプリケーション エージェントはコマンド ラインから実行することも、レプリケーション管理オブジェクト (RMO) を使用するアプリケーションから実行することもできます。 レプリケーション エージェントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターおよび [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から管理できます。  
  
## SQL Server エージェント  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントは、ホストしレプリケーションで使用するエージェントをスケジュールし、レプリケーション エージェントを実行する簡単な方法を提供します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントも管理およびレプリケーション以外の操作を監視します。 詳細については、「 [Configure SQL Server Agent](../../../ssms/agent/configure-sql-server-agent.md)」をご覧ください。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール時に、サービスがインストール中に自動開始されるように明示的に選択しない限り、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスは既定で無効になります。 開始の詳細については、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスを参照してください [開始、停止、または SQL Server エージェント サービスを一時停止](../../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)します。  
  
## スナップショット エージェント  
 スナップショット エージェントは、一般的にすべての種類のレプリケーションで使用されます。 スナップショット エージェントは、パブリッシュされたテーブルやその他のオブジェクトのスキーマと初期データ ファイルを作成し、スナップショット ファイルを格納して、同期に関する情報をディストリビューション データベースに記録します。 スナップショット エージェントはディストリビューター側で実行されます。 詳細については、次を参照してください。 [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)します。  
  
## ログ リーダー エージェント (Log Reader Agent)  
 ログ リーダー エージェントは、トランザクション レプリケーションで使用されます。 レプリケーションとしてマークが付けられたトランザクションを、パブリッシャーのトランザクション ログから、ディストリビューション データベースに移動します。 トランザクション レプリケーションを使用してパブリッシュされた各データベースには、ディストリビューター上で実行され、パブリッシャーに接続する独自のログ リーダー エージェントがあります (ディストリビューターはパブリッシャーと同じコンピューター上に存在していてもかまいません)。 詳細については、「 [Replication Log Reader Agent](../../../relational-databases/replication/agents/replication-log-reader-agent.md)」を参照してください。  
  
## ディストリビューション エージェント  
 ディストリビューション エージェントは、スナップショット レプリケーション、およびトランザクション レプリケーションで使用されます。 ディストリビューション エージェントは初期スナップショットをサブスクライバーに適用し、ディストリビューション データベースに保持されているトランザクションをサブスクライバーに移動します。 ディストリビューション エージェントは、プッシュ サブスクリプションの場合はディストリビューターで実行され、プル サブスクリプションの場合はサブスクライバーで実行されます。 詳細については、次を参照してください。 [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)します。  
  
## [マージ エージェント]  
 マージ エージェントは、マージ レプリケーションで使用されます。 マージ エージェントは、初期スナップショットをサブスクライバーに適用し、データの増分変更を移動および調整します。 マージ サブスクリプションごとにマージ エージェントがあり、パブリッシャーとサブスクライバーの両方に接続し、両方を更新します。 マージ エージェントは、プッシュ サブスクリプションの場合はディストリビューターで実行され、プル サブスクリプションの場合はサブスクライバーで実行されます。 既定では、マージ エージェントはサブスクライバーからパブリッシャーに変更をアップロードし、パブリッシャーからサブスクライバーに変更をダウンロードします。 詳細については、次を参照してください。 [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)します。  
  
## キュー リーダー エージェント (Queue Reader Agent)  
 キュー リーダー エージェントは、キュー更新オプションによるトランザクション レプリケーションで使用されます。 このエージェントはディストリビューターで実行され、サブスクライバーで行われた変更をパブリッシャーに戻します。 ディストリビューション エージェントやマージ エージェントとは異なり、キュー リーダー エージェントは 1 つのインスタンスだけで、ディストリビューション データベースのすべてのパブリッシャーおよびパブリケーションに対応します。 キュー リーダー エージェントの詳細については、次を参照してください。 [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)します。 更新可能なサブスクリプションの詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
## レプリケーション メンテナンス ジョブ  
 レプリケーションには、定期的なメンテナンスや要求時メンテナンスを実行する多数のメンテナンス ジョブがあります。 詳細については、次を参照してください。 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)します。  
  
## 参照  
 [開始および停止レプリケーション エージェントと #40 です。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [実行のレプリケーション保守ジョブと #40 です。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  