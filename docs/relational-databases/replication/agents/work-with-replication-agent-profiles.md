---
title: "レプリケーション エージェント プロファイルの操作 | Microsoft Docs"
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
  - "replication [SQL Server], agents and profiles"
  - "replication agent profiles [SQL Server]"
  - "agents [SQL Server replication], profiles"
  - "プロファイル [SQL Server], レプリケーション エージェント"
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
caps.latest.revision: 49
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 49
---
# レプリケーション エージェント プロファイルの操作
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、レプリケーション エージェント プロファイルを操作する方法について説明します。 各レプリケーション エージェントの動作は、エージェント プロファイルで設定できる一連のパラメーターによって制御されます。 各エージェントには既定のプロファイルがあり、その一部には事前に定義された追加のプロファイルがあります。1 つのエージェントに対しては、1 つのプロファイルのみがアクティブになります。  
  
 **このトピックの内容**  
  
-   **レプリケーション エージェント プロファイルを操作するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
    -   [エージェント プロファイル] ダイアログ ボックスへのアクセス  
  
    -   エージェントのプロファイルの指定  
  
    -   プロファイルの作成  
  
    -   プロファイルの変更  
  
    -   プロファイルの削除  
  
     [Transact-SQL](#TsqlProcedure)  
  
    -   プロファイルの作成  
  
    -   プロファイルの変更  
  
    -   プロファイルの削除  
  
    -   同期時のエージェント プロファイルの使用  
  
    -   Transact-SQL の例  
  
     [レプリケーション管理オブジェクト (Replication Management Objects)](#RMOProcedure)  
  
    -   プロファイルの作成  
  
    -   プロファイルの変更  
  
    -   プロファイルの削除  
  
-   **補足情報:**  [エージェントのパラメーターを変更した後](#FollowUp)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
###  <a name="Access_SSMS"></a> SQL Server Management Studio から [エージェント プロファイル] ダイアログ ボックスにアクセスするには  
  
1.   **全般** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ダイアログ ボックスで、をクリックして **プロファイルは既定で**します。  
  
#### レプリケーション モニターから [エージェント プロファイル] ダイアログ ボックスにアクセスするには  
  
-   すべてのエージェント] ダイアログ ボックスを表示する、パブリッシャーを右クリックし、をクリックして **エージェント プロファイル**します。  
  
-   単一のエージェントに対するダイアログ ボックスを開くには  
  
    1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
    2.  ディストリビューション エージェントおよびマージ エージェントのプロファイルをサブスクリプションを右クリックして、 **すべてのサブスクリプション** タブをクリックし、をクリックし、 **エージェント プロファイル**します。 その他のエージェントでエージェントを右クリックして、 **エージェント** タブをクリックし、をクリックし、 **エージェント プロファイル**します。  
  
###  <a name="Specify_SSMS"></a> エージェントのプロファイルを指定するには  
  
1.  **[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。  
  
2.  **[エージェント プロファイル]** グリッドの **[新規の既定]** 列でプロファイルを選択します。 既定では、プロファイルは、新しいパブリケーションとサブスクリプションに対するエージェントにのみ適用されます。  
  
3.  既存のパブリケーションまたはサブスクリプションに対して選択された種類のすべてのエージェントがこのプロファイルを使用するように指定するには、 **[既存のエージェントの変更]**をクリックします。  
  
###  <a name="Modify_SSMS"></a> プロファイルに関連付けられたパラメーターを表示および編集するには  
  
1.  **[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。  
  
2.  [プロパティ] ボタンをクリックして (**...**) プロファイルの横にあります。  
  
3.  パラメーターと値を表示、 **\< ProfileName> プロファイル プロパティ** ] ダイアログ ボックス。  
  
    -   ユーザー定義プロファイルのパラメーターは編集できます。事前に定義されているシステム プロファイルのパラメーターは編集できません。  
  
    -   1 つのエージェントに対するすべてのパラメーターを表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。 エージェント パラメーターの詳細については、このトピックの末尾のリンクを参照してください。  
  
4.  **[閉じる]**をクリックします。  
  
###  <a name="Create_SSMS"></a> ユーザー定義プロファイルを作成するには  
  
1.  **[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。  
  
2.  **[新規作成]**をクリックします。  
  
3.  **[新しいエージェント プロファイル]** 初期化ダイアログ ボックスで、新しいプロファイルの基となる既存のプロファイルを選択します。  
  
4.  **[新しいエージェント プロファイル]** ダイアログ ボックスで、 **[名前]** と **[説明]** ボックスに値を入力します。  
  
5.  パラメーターを変更してプロファイルを調整します。 1 つのエージェントに対するすべてのパラメーターを表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。 エージェント パラメーターの詳細については、このトピックの末尾のリンクを参照してください。  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="Delete_SSMS"></a> ユーザー定義プロファイルを削除するには  
  
1.  **[エージェント プロファイル]** ダイアログ ボックスにエージェントのプロファイルが複数表示されている場合は、エージェントを 1 つ選択します。  
  
2.  1 つのプロファイルが 1 つ以上のエージェントに関連付けられている場合は、これらのエージェントに対するプロファイルを変更します。  
  
    1.  **[エージェント プロファイル]** グリッドで別のプロファイルを選択します。  
  
    2.  **[既存のエージェントの変更]**をクリックします。  
  
        > [!NOTE]  
        >  これによって、削除したいプロファイルを使用しているエージェントだけではなく、既存のパブリケーションまたはサブスクリプションに対して選択された種類のすべてのエージェントに対するプロファイルが変更されます。  
  
3.  削除するプロファイルを選択し、 **[削除]**をクリックします。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
###  <a name="Create_tsql"></a> 新しいエージェント プロファイルを作成するには  
  
1.  ディストリビューターで実行 [sp_add_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)します。 指定 **@name**, の値 **1** の **@profile_type**, 、次のいずれかの値と **@agent_type**:  
  
    -   **1** - [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     このプロファイルがこの種類のレプリケーション エージェントの新しい既定のプロファイルになる場合、 **@default** に **1**を指定します。 使用して新しいプロファイルの識別子が返される、 **@profile_id** 出力パラメーターです。 これにより、特定の種類のエージェントの既定のプロファイルに基づいたプロファイル パラメーターのセットを備えた、新しいプロファイルが作成されます。  
  
2.  新しいプロファイルを作成したら、既定のパラメーターを追加、削除、変更してプロファイルをカスタマイズします。  
  
###  <a name="Modify_tsql"></a> 既存のエージェント プロファイルを変更するには  
  
1.  ディストリビューターで実行 [sp_help_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)します。 次の値のいずれかを指定 **@agent_type**:  
  
    -   **1** - [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     これにより、指定された種類のエージェントのプロファイルがすべて返されます。 値に注意してください **profile_id** を変更するプロファイルの結果セットにします。  
  
2.  ディストリビューターで実行 [sp_help_agent_parameter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)します。 手順 1. のプロファイル id を指定する **@profile_id**します。 これにより、プロファイルのすべてのパラメーターが返されます。 変更するパラメーター、またはプロファイルから削除するパラメーターの名前を確認します。  
  
3.  プロファイルのパラメーターの値を変更するには、実行 [sp_change_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)します。 手順 1. のプロファイル id を指定する **@profile_id**, を変更するパラメーターの名前 **@property**, 、およびパラメーターの新しい値 **@value**します。  
  
    > [!NOTE]  
    >  既存のエージェント プロファイルを変更して、エージェントの既定のプロファイルにすることはできません。 代わりに、前の手順に示すように、新しいプロファイルを既定のプロファイルとして作成する必要があります。  
  
4.  プロファイルからパラメーターを削除するには、実行 [sp_drop_agent_parameter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)します。 手順 1. のプロファイル id を指定する **@profile_id** を削除するパラメーターの名前と **@parameter_name**です。  
  
5.  プロファイルに新しいパラメーターを追加するには、次の手順を実行する必要があります。  
  
    -   クエリ、 [MSagentparameterlist & #40 です。Transact SQL と #41;](../../../relational-databases/system-tables/msagentparameterlist-transact-sql.md) 各エージェント タイプのプロファイル パラメーターを設定できるか判断する、ディストリビューター側でテーブルです。  
  
    -   ディストリビューターで実行 [sp_add_agent_parameter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)します。 手順 1. のプロファイル id を指定する **@profile_id**, に追加する有効なパラメーターの名前 **@parameter_name**, 、およびパラメーターの値 **@parameter_value**します。  
  
###  <a name="Delete_tsql"></a> エージェント プロファイルを削除するには  
  
1.  ディストリビューターで実行 [sp_help_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)します。 次の値のいずれかを指定 **@agent_type**:  
  
    -   **1** - [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     これにより、指定された種類のエージェントのプロファイルがすべて返されます。 値に注意してください **profile_id** を削除するプロファイルの結果セットにします。  
  
2.  ディストリビューターで実行 [sp_drop_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)します。 手順 1. のプロファイル id を指定する **@profile_id**します。  
  
###  <a name="Synch_tsql"></a> 同期の際にエージェント プロファイルを使用するには  
  
1.  ディストリビューターで実行 [sp_help_agent_profile & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)します。 次の値のいずれかを指定 **@agent_type**:  
  
    -   **1** - [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     これにより、指定された種類のエージェントのプロファイルがすべて返されます。 値に注意してください **profile_name** を使用するプロファイルの結果セットにします。  
  
2.  エージェントが開始されて、エージェント ジョブの場合は、値を指定する、エージェントが起動するジョブ ステップを編集 **profile_name** 後に手順 1. で得た、 **- ProfileName** コマンド ライン パラメーター。 詳細については、次を参照してください。 [表示および変更のレプリケーション エージェントのコマンド プロンプト パラメーター & #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)です。  
  
3.  コマンド プロンプトから、エージェントを開始するときにの値を指定 **profile_name** 後に手順 1. で得た、 **- ProfileName** コマンド ライン パラメーター。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、マージ エージェントがという名前のカスタム プロファイルを作成 **custom_merge**, の値を変更、 **- UploadReadChangesPerBatch** パラメーターの新しい追加 **-exchangetype** パラメーター、および作成されるプロファイルに関する情報を返します。  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../relational-databases/replication/codesnippet/tsql/work-with-replication-ag_1.sql)]  
  
##  <a name="RMOProcedure"></a> RMO の使用  
  
###  <a name="Create_RMO"></a> 新しいエージェント プロファイルを作成するには  
  
1.  インスタンスを使用してディストリビューターに接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.AgentProfile> クラスです。  
  
3.  オブジェクトの次のプロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> -プロファイルの名前。  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - <xref:Microsoft.SqlServer.Replication.AgentType> プロファイルが作成されているレプリケーション エージェントの種類を指定する値。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。  
  
    -   (省略可能) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> -プロファイルの説明。  
  
    -   (省略可能) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> -このプロパティを設定 **true** 場合はこの新しいエージェント ジョブをすべて <xref:Microsoft.SqlServer.Replication.AgentType> 既定では、このプロファイルを使用します。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> サーバーで、プロファイルを作成します。  
  
5.  サーバーにプロファイルが作成されたら、レプリケーション エージェントのパラメーター値を追加、削除、変更することで、プロファイルをカスタマイズできます。  
  
6.  プロファイルを既存のレプリケーション エージェント ジョブに割り当てるには、呼び出し、 <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> メソッドです。 ディストリビューション データベースの名前を *distributionDBName* に渡し、ジョブの ID を *agentID*に渡します。  
  
###  <a name="Modify_RMO"></a> 既存のエージェント プロファイルを変更するには  
  
1.  インスタンスを使用してディストリビューターに接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 渡す、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成されたオブジェクト。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、ディストリビューターが存在するかどうかを確認してください。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> メソッドです。 渡す、 <xref:Microsoft.SqlServer.Replication.AgentType> を絞り込むには、特定の種類のレプリケーション エージェント プロファイルが返される値。  
  
5.  必要な取得 <xref:Microsoft.SqlServer.Replication.AgentProfile> から返されたオブジェクト <xref:System.Collections.ArrayList>, ここで、 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> オブジェクトのプロパティには、プロファイル名が一致します。  
  
6.  次のメソッドの 1 つを呼び出して <xref:Microsoft.SqlServer.Replication.AgentProfile> プロファイルを変更します。  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> -、プロファイルにサポートされているパラメーターを追加、 *名前* レプリケーション エージェント パラメーターの名前を指定し、 *値* 指定されている値。 指定されたエージェントの種類のすべてのサポートされているエージェント パラメーターを列挙するを呼び出す、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> メソッドです。 このメソッドが戻る、 <xref:System.Collections.ArrayList> の <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> サポートされているすべてのパラメーターを表すオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> -プロファイルから既存のパラメーターを削除、 *名前* レプリケーション エージェント パラメーターの名前を指定します。 プロファイルに対して定義されている現在のすべてのエージェント パラメーターを列挙するを呼び出して、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> メソッドです。 このメソッドが戻る、 <xref:System.Collections.ArrayList> の <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> このプロファイルの既存のパラメーターを表すオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> -プロファイルでは、既存のパラメーターの設定を変更、 *名前* エージェント パラメーターの名前を指定し、 *newValue* パラメーターが変更されている値は、です。 プロファイルに対して定義されている現在のすべてのエージェント パラメーターを列挙するを呼び出して、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> メソッドです。 このメソッドが戻る、 <xref:System.Collections.ArrayList> の <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> このプロファイルの既存のパラメーターを表すオブジェクト。 サポートされるエージェント パラメーターの設定をすべて列挙する、呼び出し、 <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> メソッドです。 このメソッドが戻る、 <xref:System.Collections.ArrayList> の <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> サポートされるすべてのパラメーターの値を表すオブジェクト。  
  
###  <a name="Delete_RMO"></a> エージェント プロファイルを削除するには  
  
1.  インスタンスを使用してディストリビューターに接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.AgentProfile> クラスです。 プロファイルの名前を設定 <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> と <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、指定された名前が誤っているか、プロファイルがサーバーに存在していません。  
  
4.  いることを確認、 <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> にプロパティが設定されている <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, 、顧客のプロファイルを示します。 値を持つプロファイルを削除しないでください <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> の <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>します。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> サーバーからこのオブジェクトによって表されるユーザー定義プロファイルを削除するメソッドです。  
  
##  <a name="FollowUp"></a> フォロー アップ: エージェント パラメーターを変更した後  
 エージェント パラメーターの変更は、エージェントの次回起動時に反映されます。 エージェントを継続して実行している場合は、そのエージェントを停止して再起動する必要があります。  
  
## 参照  
 [レプリケーション エージェント プロファイル](../../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
  