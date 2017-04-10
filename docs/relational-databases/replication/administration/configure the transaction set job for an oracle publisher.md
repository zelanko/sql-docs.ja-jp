---
title: "Oracle パブリッシャー用のトランザクション セット ジョブの構成 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_publisherproperty"
  - "Oracle パブリッシング [SQL Server レプリケーション]、構成"
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Oracle パブリッシャー用のトランザクション セット ジョブの構成 (レプリケーション Transact-SQL プログラミング)
   **Xactset** ジョブは、ログ リーダー エージェントがパブリッシャーに接続されていない場合は、トランザクション セットを作成する、Oracle パブリッシャーで実行されるレプリケーションによって作成された Oracle データベース ジョブです。 このジョブは、レプリケーションのストアド プロシージャを使用し、ディストリビューターからプログラムによって有効化したり構成することができます。 詳細については、次を参照してください。 [Oracle パブリッシャーのパフォーマンス チューニング](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)します。  
  
### トランザクション セット ジョブを有効にするには  
  
1.  Oracle パブリッシャーでは、設定、 **job_queue_processes** Xactset ジョブの実行を許可するための十分な値に初期化パラメーター。 このパラメーターの詳細については、Oracle パブリッシャー用データベースのマニュアルを参照してください。  
  
2.  ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 Oracle パブリッシャーの名前を指定 **@publisher**, の値 **xactsetbatching** の **@propertyname**, の値との **有効になっている** の **@propertyvalue**します。  
  
3.  ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 Oracle パブリッシャーの名前を指定 **@publisher**, の値 **xactsetjobinterval** の **@propertyname**, 、およびジョブの実行間隔を分単位での **@propertyvalue**します。  
  
4.  ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 Oracle パブリッシャーの名前を指定 **@publisher**, の値 **xactsetjob** の **@propertyname**, の値との **有効になっている** の **@propertyvalue**します。  
  
### トランザクション セット ジョブを構成するには  
  
1.  (省略可能)ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 **@publisher**に Oracle パブリッシャーの名前を指定します。 プロパティが返されます、 **Xactset** 、パブリッシャー側でのジョブです。  
  
2.  ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 Oracle パブリッシャーの名前を指定 **@publisher**, に設定されている Xactset ジョブ プロパティの名前 **@propertyname**, の新しい設定と **@propertyvalue**します。  
  
3.  (省略可) 設定対象の各 Xactset ジョブ プロパティについて、手順 2. を繰り返します。 変更するときに、 **xactsetjobinterval** プロパティには、新しい間隔を有効にする Oracle パブリッシャーでジョブを再起動する必要があります。  
  
### トランザクション セット ジョブのプロパティを表示するには  
  
1.  ディストリビューターで実行 [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md)します。 **@publisher**に Oracle パブリッシャーの名前を指定します。  
  
### トランザクション セット ジョブを無効にするには  
  
1.  ディストリビューターで実行 [sp_publisherproperty & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)します。 Oracle パブリッシャーの名前を指定 **@publisher**, の値 **xactsetjob** の **@propertyname**, の値との **無効になっている** の **@propertyvalue**します。  
  
## 例  
 次の例では、`Xactset` ジョブを有効にし、実行間隔を 3 分に設定しています。  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## 参照  
 [Oracle パブリッシャーのパフォーマンス チューニング](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  