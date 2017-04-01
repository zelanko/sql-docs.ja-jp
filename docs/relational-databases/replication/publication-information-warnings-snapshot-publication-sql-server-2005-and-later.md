---
title: "パブリケーション情報、[警告] (スナップショット パブリケーション、SQL Server 2005 以降) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.warningsandagents.snapshot.f1"
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# パブリケーション情報、[警告] (スナップショット パブリケーション、SQL Server 2005 以降)
  **以降を実行しているディストリビューターでは、** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。 **[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。  
  
-   警告を有効にする。  
  
-   警告に関連するしきい値を指定する。  
  
-   警告に関連する通知を定義する。  
  
## 警告、しきい値、および通知  
 既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。 スナップショット パブリケーションに指定することもが迫っていないかのサブスクリプションの有効期限オプションを設定して、警告に結果 **警告しきい値内で、サブスクリプションは期限が切れます**します。 サブスクリプションの状態が [として表示されている場合は、指定したしきい値に達するか超過は、 **まもなく期限切れ/期限切れ** (限り、優先順位の高い問題を表示する必要があります)。  
  
 しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。 通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。  
  
## オプション  
 **有効**  
 警告を有効にする場合に選択します。その場合は、しきい値を指定します。  
  
 **警告**  
 しきい値に関連付けられている警告の説明です。  
  
 **しきい値**  
 しきい値の値を指定します。  
  
 **[警告の構成]**  
 内の行を選択して、 **警告** グリッド、およびクリック **アラートの構成** を起動する、 **[レプリケーションの警告** ] ダイアログ ボックス。 このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。  
  
 **[変更の破棄]**  
 クリックすると、警告およびしきい値に対する変更が破棄されます。  
  
> [!NOTE]  
>  クリックすると **変更を破棄する** で定義されているアラートには影響しません、 **[レプリケーションの警告** ] ダイアログ ボックス。  
  
 **[変更の保存]**  
 クリックすると、警告およびしきい値に対する変更が保存されます。  
  
## 参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [情報を表示し、パブリケーションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  