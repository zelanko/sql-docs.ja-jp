---
title: "マージ パブリケーションでのデータの競合の表示および解決 (SQL Server Management Studio) | Microsoft Docs"
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
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション], 競合の表示"
  - "競合情報の表示"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ パブリケーションでのデータの競合の表示および解決 (SQL Server Management Studio)
  マージ レプリケーションの競合は、各アーティクルに対して指定された競合回避モジュールに基づいて解決されます。 既定では、競合はユーザーの介入を必要とせずに解決されます。 ただし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] レプリケーション競合表示モジュールで競合を表示したり、解決の結果を変更したりすることができます。  
  
 競合データは、競合の保有期間に指定した期間内 (既定では 14 日間) はレプリケーション競合表示モジュールで利用できます。 競合の保有期間を設定するには、次のいずれかを実行します。  
  
-   保有期間の値を指定して、 **@conflict_retention** のパラメーター [sp_addmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。  
  
-   値を指定して **conflict_retention** の **@property** パラメーターと保有期間の値が、 **@value** のパラメーター [sp_changemergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。  
  
 競合情報の既定の保存先は次のとおりです。  
  
-   パブリケーションの互換性レベルが 90 RTM 以上の場合は、パブリッシャーおよびサブスクライバーに保存されます。  
  
-   パブリケーションの互換性レベルが 80 RTM 未満の場合は、パブリッシャーに保存されます。  
  
-   サブスクライバーが [!INCLUDE[ssEW](../../includes/ssew-md.md)] を実行している場合は、パブリッシャーに保存されます。 競合データは保管できません [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーです。  
  
 競合情報の記憶域? 궸뫮궢궲궵궻믴뱗똛궚귞귢귡궔궼갂 _aspect、 **conflict_logging** パブリケーションのプロパティです。 詳細については、次を参照してください。 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)  [sp_changemergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。  
  
 競合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] のインタラクティブ競合回避モジュールを使用して、同期実行時に対話的に解決することもできます。 インタラクティブ競合回避モジュールは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーで利用できます。 詳細については、次を参照してください [サブスクリプションを使用して Windows 同期マネージャーと #40; の同期。Windows 同期マネージャーと #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)します。  
  
### マージ パブリケーションで競合を表示および解決するには  
  
1.  パブリッシャー (または必要に応じてサブスクライバー) への接続で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして競合を表示するパブリケーションを右クリックして **の競合の表示**します。  
  
    > [!NOTE]  
    >  値を指定した場合 **'subscriber'** の **conflict_logging** プロパティには、 **の競合の表示** メニュー オプションは使用できません。 競合を表示するには、コマンド プロンプトで ConflictViewer.exe を起動します。 既定では、ConflictViewer.exe が格納されているディレクトリは、Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE です。 有効な起動時のパラメーターの一覧を表示するには、ConflictViewer.exe -? を実行します。  
  
4.   **競合テーブルの選択** ダイアログ ボックスで、パブリケーション、データベースを選択し、競合を表示する対象のテーブルです。  
  
5.  レプリケーション競合表示モジュールでは、以下を実行できます。  
  
    -   上のグリッドの右側のボタンで行をフィルター選択する。  
  
    -   上のグリッドで行を選択して、下のグリッドにその行の情報を表示する。  
  
    -   上のグリッドで 1 つまたは複数の行を選択し、クリックして **削除**, 、] をクリックすると同じ、 **送信勝者** (変更を加えずにすべてのデータに) ボタンをクリックします。  
  
    -   プロパティ] をクリックします。 (**...**) 列の詳細を表示するには、競合に関係します。  
  
    -   データの編集、 **競合で優先された** または **競合で優先されない** (データは、列がグレーの場合は読み取り専用) データを送信する前に列です。  
  
    -   をクリックして **送信勝者** 競合で優先されるデータとして指定された行を受け入れます。  
  
    -   をクリックして **で優先されなかったデータを送信** 解像度をオーバーライドし、トポロジ内のすべてのノードに競合で優先されなかったデータとして指定された値を反映します。  
  
    -   選択 **この競合の詳細を記録** 競合データをファイルに記録します。 ファイルの場所を指定する] をポイント、 **ビュー** ] メニューの [クリックして **オプション**します。 値を入力または参照ボタンをクリックして (**...**)、適切なファイルに移動します。 クリックして **OK** を終了する、 **オプション** ] ダイアログ ボックス。  
  
6.  レプリケーション競合表示モジュールを閉じます。  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [マージ アーティクル競合回避モジュールの指定](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  