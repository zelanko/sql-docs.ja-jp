---
title: "同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "同期 [SQL Server レプリケーション], スクリプト"
  - "スクリプト [SQL Server レプリケーション], 同期および"
  - "sp_addscriptexec"
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# 同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)
  レプリケーションでは、トランザクション パブリケーションおよびマージ パブリケーションのサブスクライバーに対し、要求時にスクリプトを実行できます。 この機能は、レプリケーション作業ディレクトリにスクリプトをコピーし、使用 **sqlcmd** 、サブスクライバーでスクリプトを適用します。 トランザクション パブリケーションのサブスクリプションに対してスクリプトを適用しているときにエラーが発生した場合、既定では、ディストリビューション エージェントの実行が停止します。 レプリケーションのストアド プロシージャを使用すると、指定した [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをプログラムから実行できます。  
  
### スナップショット、トランザクション、マージ パブリケーションのすべてのサブスクライバーに対して実行するスクリプトを指定するには  
  
1.  要求時に実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成およびテストします。  
  
2.  スクリプト ファイルを、パブリケーションのスナップショット エージェントがアクセスできる場所に保存します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addscriptexec & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md)します。 指定 **@publication**, 、手順 2 で作成した完全な UNC パスとスクリプト ファイルの名前 **@scriptfile**, 、次のいずれかの値と **@skiperror**:  
  
    -   **0** -エージェントは、エラーが発生した場合、スクリプトの実行を停止します。  
  
    -   **1** -エージェントはエラー ログに記録され、エラーが発生したときに、スクリプトの実行を続行します。  
  
4.  指定したスクリプトは、エージェントが次にサブスクリプションを同期するときに、各サブスクライバーで実行されます。  
  
## 参照  
 [データの同期](../../relational-databases/replication/synchronize-data.md)  
  
  