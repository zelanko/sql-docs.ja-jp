---
title: "トランザクション パブリケーションのデータの競合の表示 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "競合解決 [SQL Server レプリケーション], キュー更新サブスクリプション"
  - "キュー更新サブスクリプション [SQL Server レプリケーション]"
  - "競合情報の表示"
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# トランザクション パブリケーションのデータの競合の表示 (SQL Server Management Studio)
  ピア ツー ピア トランザクション レプリケーション、およびキュー更新サブスクリプションを使用するトランザクション レプリケーションでの競合を、[!INCLUDE[msCoName](../../includes/msconame-md.md)] レプリケーション競合表示モジュールで表示できます。 競合の検出および解決方法については、次を参照してください。 [ピア ツー ピア レプリケーションで競合検出](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md) と [キューに置かれた更新の競合解決オプションの設定と #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)します。  
  
 競合データを表示できるかどうかは、レプリケーションの種類および競合の保有期間によって異なります。  
  
-   ピア ツー ピア レプリケーションの場合、ディストリビューション エージェントは、競合を検出すると既定で停止します。 競合エラーはエラー ログに記録されますが、競合データは競合テーブルに記録されないため、競合データを表示できません。 ディストリビューション エージェントが実行の継続を許可されている場合は、競合が検出された各ノードで、競合がローカルでログに記録されます。 詳細については、競合の処理」を参照してください [ピア ツー ピア レプリケーションで競合検出](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md)します。  
  
-   キュー更新サブスクリプションの場合は、すべての競合のデータを表示できます。 競合データは、競合の保有期間に指定した期間 (既定では 14 日間)、レプリケーション競合表示モジュールで表示できます。 競合の保有期間を設定するには、次のいずれかを実行します。  
  
    -   @Conflict_retention パラメーターに保有期間の値を指定 [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。  
  
    -   値を指定して **'conflict_retention'** 、@property パラメーターと保有期間の値の @value パラメーターに [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)します。  
  
### 競合を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で適切なサーバーに接続し、そのサーバー ノードを展開します。  
  
    -   ピア ツー ピア レプリケーションの場合は、競合の発生したノードがこれに当たります。  
  
    -   キュー更新サブスクリプションの場合は、パブリッシャーがこれに当たります。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして競合を表示するパブリケーションを右クリックして **の競合の表示**します。  
  
4.   **競合テーブルの選択** ダイアログ ボックスで、パブリケーション、データベースを選択し、競合を表示する対象のテーブルです。  
  
5.  レプリケーション競合表示モジュールでは、以下を実行できます。  
  
    -   上のグリッドの右側のボタンで行をフィルター選択する。  
  
    -   上のグリッドで行を選択して、下のグリッドにその行の情報を表示する。  
  
    -   上のグリッドで 1 つまたは複数の行を選択し、クリックして **削除**, 、これは、競合メタデータ テーブルから行を削除します。  
  
    -   プロパティ] をクリックします。 (**...**) 列の詳細を表示するには、競合に関係します。  
  
    -   選択 **この競合の詳細を記録** 競合データをファイルに記録します。 ファイルの場所を指定する] をポイント、 **ビュー** ] メニューの [クリックして **オプション**します。 値を入力または参照ボタンをクリックして (**...**)、適切なファイルに移動します。 をクリックして **OK** を閉じる、 **オプション** ] ダイアログ ボックス。  
  
6.  レプリケーション競合表示モジュールを閉じます。  
  
## 参照  
 [ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [キュー更新における競合の検出と解決](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)  
  
  