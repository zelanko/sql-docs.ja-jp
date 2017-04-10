---
title: "同期スケジュールの指定 | Microsoft Docs"
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
  - "subscriptions [SQL Server replication], synchronizing"
  - "scheduling synchronization [SQL Server replication]"
  - "synchronization [SQL Server replication], schedules"
  - "レプリケーション [SQL Server], 同期"
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# 同期スケジュールの指定
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、同期スケジュールを指定する方法について説明します。 サブスクリプションを作成するときに、サブスクリプションのレプリケーション エージェントをいつ実行するかを制御する同期スケジュールを定義できます。 スケジュール設定のパラメーターを指定しなかった場合、サブスクリプションは既定のスケジュールを使用します。  
  
 サブスクリプションは、ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) で同期されます。 エージェントは継続的に実行、要求時に実行、またはスケジュールで実行できます。  
  
 **このトピックの内容**  
  
-   **同期スケジュールを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションの新規作成ウィザードの **[同期スケジュール]** ページで同期スケジュールを指定します。 このウィザードへのアクセスの詳細については、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md) 」および「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
 **[ジョブ スケジュールのプロパティ]** ダイアログ ボックスで同期スケジュールを変更します。このダイアログ ボックスは、 **の** [ジョブ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] フォルダーおよびレプリケーション モニターのエージェントの詳細ウィンドウから使用できます。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
 **[ジョブ]** フォルダーからスケジュールを指定する場合は、次の表でエージェントのジョブ名を確認してください。  
  
|エージェント|ジョブ名|  
|-----------|--------------|  
|プル サブスクリプションに対するマージ エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< SubscriptionDatabase>-\< integer>**|  
|プッシュ サブスクリプションに対するマージ エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>**|  
|プッシュ サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>** <sup>1</sup>|  
|プル サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< SubscriptionDatabase>-\< GUID>** <sup>2</sup>|  
|SQL Server 以外のサブスクライバーへのプッシュ サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>**|  
  
 <sup>1</sup> Oracle パブリケーションに対するプッシュ サブスクリプションの場合は **\< パブリッシャー>-\< Publisher**> なく **\< パブリッシャー>-\< PublicationDatabase>**  
  
 <sup>2</sup> Oracle パブリケーションに対するプル サブスクリプションの場合は **\< パブリッシャー>-\< DistributionDatabase**> なく **\< パブリッシャー>-\< PublicationDatabase>**  
  
#### 同期スケジュールを指定するには  
  
1.   **SynchronizationSchedule** の新規作成ウィザードで、次のいずれかの値から選択] ページ、 **エージェント スケジュール** ドロップダウン リストを作成する各サブスクリプションについて。  
  
    -   **[連続実行する]**  
  
    -   **[要求時にのみ実行する]**  
  
    -   **[\<スケジュールの定義>]**  
  
2.  選択した場合 **\< スケジュールの定義… >**, でスケジュールを指定する、 **ジョブ スケジュールのプロパティ** クリックしてダイアログ ボックスで、 **[ok]**します。  
  
3.  ウィザードを完了します。  
  
#### レプリケーション モニターでプッシュ サブスクリプションの同期スケジュールを変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **の詳細の表示**します。  
  
4.   **サブスクリプション \< SubscriptionName >** ウィンドウで、をクリックして **アクション**, 、] をクリックし、 **\< AgentName> ジョブのプロパティ**します。  
  
5.   **スケジュール** のページ、 **ジョブのプロパティ - \< JobName>** ダイアログ ボックスで、をクリックして **を編集します。**  
  
6.   **ジョブ スケジュールのプロパティ** 値を選択します] ダイアログ ボックスで、 **スケジュールの種類** ボックスの一覧。  
  
    -   エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]**を選択します。  
  
    -   エージェントをスケジュールで実行するには、 **[定期的]**を選択します。  
  
    -   エージェントを要求時に実行するには、 **[指定日時]**を選択します。  
  
7.  **[定期的]**を選択した場合は、エージェントのスケジュールを指定します。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Management Studio でプッシュ サブスクリプションの同期スケジュールを変更するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ディストリビューション エージェントまたはマージ エージェントが、サブスクリプションに関連付けられているジョブを右クリックし、クリックして **プロパティ**します。  
  
4.   **スケジュール** のページ、 **ジョブのプロパティ - \< JobName>** ダイアログ ボックスで、をクリックして **を編集します。**  
  
5.   **ジョブ スケジュールのプロパティ** 値を選択します] ダイアログ ボックスで、 **スケジュールの種類** ボックスの一覧。  
  
    -   エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]**を選択します。  
  
    -   エージェントをスケジュールで実行するには、 **[定期的]**を選択します。  
  
    -   エージェントを要求時に実行するには、 **[指定日時]**を選択します。  
  
6.  **[定期的]**を選択した場合は、エージェントのスケジュールを指定します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### Management Studio でプル サブスクリプションの同期スケジュールを変更するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ディストリビューション エージェントまたはマージ エージェントが、サブスクリプションに関連付けられているジョブを右クリックし、クリックして **プロパティ**します。  
  
4.   **スケジュール** のページ、 **ジョブのプロパティ - \< JobName>** ダイアログ ボックスで、をクリックして **を編集します。**  
  
5.   **ジョブ スケジュールのプロパティ** 値を選択します] ダイアログ ボックスで、 **スケジュールの種類** ボックスの一覧。  
  
    -   エージェントを連続実行するには、 **[SQL Server エージェントの開始時に自動的に開始]**を選択します。  
  
    -   エージェントをスケジュールで実行するには、 **[定期的]**を選択します。  
  
    -   エージェントを要求時に実行するには、 **[指定日時]**を選択します。  
  
6.  **[定期的]**を選択した場合は、エージェントのスケジュールを指定します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用してプログラムで同期スケジュールを定義できます。 使用するストアド プロシージャは、レプリケーションの種類およびサブスクリプションの種類 (プルまたはプッシュ) によって異なります。  
  
 次のスケジュール パラメーターから継承する動作で、スケジュールが定義されている [sp_add_schedule & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md):  
  
-   **@frequency_type** -エージェントのスケジュール設定するときに使用頻度の種類。  
  
-   **@frequency_interval** - エージェントを実行する曜日。  
  
-   **@frequency_relative_interval** - 毎月実行する、エージェントをスケジュールするときに指定された月の週。  
  
-   **@frequency_recurrence_factor** -同期中に発生する頻度の種類の単位の数。  
  
-   **@frequency_subday** -エージェントが 1 日に 1 回よりも頻繁に実行すると、頻度の単位です。  
  
-   **@frequency_subday_interval** -頻度の単位の数が、エージェントが 1 日に 1 回よりも頻繁に実行されるときに実行します。  
  
-   **@active_start_time_of_day** - 指定した日のエージェントの実行を開始する最も早い時刻。  
  
-   **@active_end_time_of_day** - 最新の時刻で指定した日のエージェントの実行を開始します。  
  
-   **@active_start_date** - エージェントのスケジュールを有効にする最初の日。  
  
-   **@active_end_date** - エージェントのスケジュールを有効にする最後の日。  
  
#### トランザクション パブリケーションに対するプル サブスクリプションの同期スケジュールを定義するには  
  
1.  トランザクション パブリケーションに対して新しいプル サブスクリプションを作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addpullsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、および [!INCLUDE[msCoName](../../includes/msconame-md.md)] のサブスクライバーでディストリビューション エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 サブスクリプションを同期するディストリビューション エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。  
  
#### トランザクション パブリケーションに対するプッシュ サブスクリプションの同期スケジュールを定義するには  
  
1.  トランザクション パブリケーションに対して新しいプッシュ サブスクリプションを作成します。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addpushsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)します。 指定 **@subscriber**, 、**@subscriber_db**, 、**@publication**, 、およびサブスクライバーでディストリビューション エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 サブスクリプションを同期するディストリビューション エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。  
  
#### マージ パブリケーションに対するプル サブスクリプションの同期スケジュールを定義するには  
  
1.  マージ パブリケーションに対して新しいプル サブスクリプションを作成します。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、およびサブスクライバーでマージ エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 サブスクリプションを同期するマージ エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションの同期スケジュールを定義するには  
  
1.  マージ パブリケーションに対して新しいプッシュ サブスクリプションを作成します。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)します。 指定 **@subscriber**, 、**@subscriber_db**, 、**@publication**, 、およびサブスクライバーでマージ エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 サブスクリプションを同期するマージ エージェント ジョブのスケジュールを定義する、上述の同期のパラメーターを指定します。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーションは、SQL&amp;#xA0;Server エージェントを使用して、スナップショットの生成やサブスクリプションの同期など、定期的に発生する動作のジョブをスケジュール設定します。 レプリケーション管理オブジェクト (RMO) をプログラムで使用して、レプリケーション エージェント ジョブのスケジュールを指定できます。  
  
> [!NOTE]  
>  サブスクリプションを作成し、値を指定して **false** の **CreateSyncAgentByDefault** (プル サブスクリプションの既定の動作)、エージェント ジョブは作成されず、スケジュール設定のプロパティは無視されます。 この場合は、アプリケーションによって同期スケジュールを決定する必要があります。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 」および「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」を参照してください。  
  
#### トランザクション パブリケーションに対するプッシュ サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには  
  
1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> 、サブスクリプションを作成するためのクラスです。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
2.  呼び出す前に <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, 、1 つ以上の次のフィールドの設定、 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> プロパティ。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -エージェントのスケジュールを設定するときに使用する頻度 (毎日または毎週) などの種類。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 毎月実行する、エージェントをスケジュールするときに指定された月の週。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -同期中に発生する頻度の種類の単位の数。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -エージェントが 1 日に 1 回よりも頻繁に実行すると、頻度の単位です。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -頻度の単位の数が、エージェントが 1 日に 1 回よりも頻繁に実行されるときに実行します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。  
  
    > [!NOTE]  
    >  これらのプロパティを指定しなかった場合、既定値が設定されます。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> サブスクリプションを作成します。  
  
#### トランザクション パブリケーションに対するプル サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには  
  
1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 、サブスクリプションを作成するためのクラスです。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
2.  呼び出す前に <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, 、1 つ以上の次のフィールドの設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> プロパティ。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -エージェントをスケジュールするときに使用する頻度 (毎日または毎週) などの種類。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 毎月実行する、エージェントがスケジュールされている指定された月の週。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -同期中に発生する頻度の種類の単位の数。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -エージェントが 1 日に 1 回よりも頻繁に実行すると、頻度の単位です。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -頻度の単位の数が、エージェントが 1 日に 1 回よりも頻繁に実行されるときに実行します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。  
  
    > [!NOTE]  
    >  これらのプロパティを指定しなかった場合、既定値が設定されます。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> サブスクリプションを作成します。  
  
#### マージ パブリケーションに対するプル サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには  
  
1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 、サブスクリプションを作成するためのクラスです。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
2.  呼び出す前に <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, 、1 つ以上の次のフィールドの設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> プロパティ。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -エージェントをスケジュールするときに使用する頻度 (毎日または毎週) などの種類。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 毎月実行する、エージェントがスケジュールされている指定された月の週。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -同期中に発生する頻度の種類の単位の数。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -エージェントが 1 日に 1 回よりも頻繁に実行すると、頻度の単位です。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -頻度の単位の数が、エージェントが 1 日に 1 回よりも頻繁に実行されるときに実行します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。  
  
    > [!NOTE]  
    >  これらのプロパティを指定しなかった場合、既定値が設定されます。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> サブスクリプションを作成します。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを作成するレプリケーション エージェント スケジュールを定義するには  
  
1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 、サブスクリプションを作成するためのクラスです。 詳しくは、「 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)」をご覧ください。  
  
2.  呼び出す前に <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, 、1 つ以上の次のフィールドの設定、 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> プロパティ。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> -エージェントをスケジュールするときに使用する頻度 (毎日または毎週) などの種類。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - エージェントを実行する曜日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 毎月実行する、エージェントがスケジュールされている指定された月の週。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> -同期中に発生する頻度の種類の単位の数。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> -エージェントが 1 日に 1 回よりも頻繁に実行すると、頻度の単位です。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> -頻度の単位の数が、エージェントが 1 日に 1 回よりも頻繁に実行されるときに実行します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - エージェントの実行を開始する特定の日の最も早い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - エージェントの実行を開始する特定の日の最も遅い時刻。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - エージェント スケジュールが有効になっている最初の日。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - エージェント スケジュールが有効になっている最後の日。  
  
    > [!NOTE]  
    >  これらのプロパティを指定しなかった場合、既定値が設定されます。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> サブスクリプションを作成します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、マージ パブリケーションに対するプッシュ サブスクリプションを作成して、サブスクリプションを同期するスケジュールを指定します。  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## 参照  
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)   
 [データの同期](../../relational-databases/replication/synchronize-data.md)  
  
  