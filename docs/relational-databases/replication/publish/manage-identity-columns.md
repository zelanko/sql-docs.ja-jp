---
title: "ID 列の管理 | Microsoft Docs"
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
  - "ID 値 [SQL Server レプリケーション]"
  - "マージ レプリケーション [SQL Server レプリケーション], ID 範囲の管理"
  - "パブリッシング [SQL Server レプリケーション], ID 列"
  - "トランザクション レプリケーション, ID 範囲の管理"
  - "ID 列 [SQL Server], レプリケーション"
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# ID 列の管理
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、ID 列を管理する方法について説明します。 サブスクライバー挿入がパブリッシャーにレプリケートされる場合、サブスクライバーとパブリッシャーに同じ ID 値が割り当てられないように、ID 列を管理する必要があります。 レプリケーションでは ID の範囲を自動的に管理することも、ID の範囲を手動で管理することもできます。  レプリケーションによって提供される id 範囲管理オプションについては、次を参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **ID 列を管理するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   複数のパブリケーションでテーブルをパブリッシュする場合、両方のパブリケーションに同じ ID 範囲管理オプションを指定する必要があります。 詳細については、「テーブルより 1 つのパブリケーションでパブリッシュ」を参照してください [発行データおよびデータベース オブジェクト](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)します。  
  
-   複数のテーブルで使用できるかを任意のテーブルを参照することがなくアプリケーションから呼び出すことは、自動的に増分する番号を作成するを参照してください。 [シーケンス番号](../../../relational-databases/sequence-numbers/sequence-numbers.md)です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 Id] 列の管理オプションを指定、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** パブリケーションの新規作成ウィザードのダイアログ ボックス。 このウィザードの使用に関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。 パブリケーションの新規作成ウィザードで選択した内容に応じて、次の操作を行います。  
  
-   選択した場合 **マージ パブリケーション** または **更新サブスクリプションを含むトランザクション パブリケーション** 上、 **パブリケーションの種類** ページで、自動または手動による id 範囲管理を選択 (自動で、既定値を推奨)。 このプロパティは、テーブルがパブリッシュされた後は変更できません。ただし、その他の関連プロパティは変更できます。  
  
-   他のパブリケーションの種類を選択した場合は、ID 範囲の管理を手動に設定する必要があります。  
  
 Id 範囲としきい値を変更、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>**, に用意されている、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
#### ID 列の管理オプションを指定するには  
  
1.  パブリッシャーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]を実行している場合は、パブリケーションの新規作成ウィザードの **[パブリケーションの種類]** ページで、 **[マージ パブリケーション]** または **[更新可能なサブスクリプションを含むトランザクション パブリケーション]**を選択します。  
  
2.  **[アーティクル]** ページで、ID 列があるテーブルを選択します。  
  
3.  **[アーティクルのプロパティ]**をクリックしてから、 **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
4.   **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ダイアログ ボックスで、 **Id 範囲管理** セクションで、設定、 **id 範囲を自動的に管理** プロパティを **自動** または **手動** (実行しているパブリッシャーの [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] またはそれ以降)、または **True** または **False** (のバージョンを実行しているパブリッシャーの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のバージョン [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)])。  
  
5.  手順 4. で **[自動]** または **[True]** を選択した場合は、次の表のオプションの値を入力します。 これらの設定の使用方法の詳細については、の「Id 範囲の割り当て」セクションを参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
    |オプション|値|説明|  
    |------------|-----------|-----------------|  
    |**[パブリッシャーの範囲サイズ]**|範囲サイズの整数値 (たとえば 20000)。|「Id 範囲の割り当て」を参照してください [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
    |**[サブスクライバーの範囲サイズ]**|範囲サイズの整数値 (たとえば 10000)。|「Id 範囲の割り当て」を参照してください [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
    |**[範囲しきい値の割合]**|パーセントによるしきい値の整数値 (たとえば、90 は 90% を表します)。|ノードで使用されている ID 値全体の比率がこの値を超えると、新しい ID 範囲が割り当てられます。<br /><br /> <br /><br /> 注: この値の指定は必須ですが、この値を使用するのは、キュー更新サブスクリプションを使用するサブスクライバーと、 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] または他のエディションの SQL Server の旧バージョンを実行しているマージ パブリケーションのサブスクライバーだけです。 詳細については、の「Id 範囲の割り当て」セクションを参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
    |**[次の範囲の開始値]**|整数値。 読み取り専用です。|次の範囲はこの値から始まります。 たとえば、現在の範囲が 5001 ～ 6000 の場合、この値は 6001 になります。|  
    |**[最大 ID 値]**|整数値。 読み取り専用です。|ID 列の最大値です。 列の基本データ型によって決まります。|  
    |**Increment**|整数値。 読み取り専用です。|挿入のたびに ID 列の番号が増減する量。通常は 1 に設定されます。|  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### テーブルがパブリッシュされた後に ID 範囲としきい値を変更するには  
  
1.   **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、id 列を持つテーブルを選択します。  
  
2.  **[アーティクルのプロパティ]**をクリックしてから、 **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ダイアログ ボックスで、 **Id 範囲管理** セクションで、次のプロパティの 1 つ以上の値を入力: **パブリッシャーの範囲サイズ**, 、**サブスクライバーの範囲サイズ**, と **しきい値 (%) の範囲**します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  をクリックして **OK** 上、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用して、アーティクルを作成するときの ID 範囲管理オプションを指定できます。  
  
#### トランザクション パブリケーションのアーティクルを定義する際に自動 ID 範囲管理を有効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 パブリッシュされているソース テーブルに id 列がある場合は、値を指定 **自動** の **@identityrangemanagementoption**, のパブリッシャーに割り当てられる id 値の範囲 **@pub_identity_range**, の各サブスクライバーに割り当てられる id 値の範囲 **@identity_range**, 、に対して新しい id 範囲が割り当てられる前に使用される合計 id 値の割合と **@threshold**します。 詳細については、アーティクルを定義する、次を参照してください。 [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
    > [!NOTE]  
    >  ID 列のデータ型のサイズが、すべてのサブスクライバーに割り当てられる ID 範囲の総計をサポートできるだけの大きさであることを確認してください。  
  
#### トランザクション パブリケーションのアーティクルを定義する際に自動 ID 範囲管理を無効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 **@identityrangemanagementoption** に **manual**を指定します。 詳細については、アーティクルを定義する、次を参照してください。 [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
2.  サブスクライバーの更新時に競合が発生しないように、サブスクライバーの ID アーティクル列に範囲を割り当てます。 詳細については、手動で id 範囲管理のトピックでの範囲を割り当てる方法に関するセクションを参照してください。 [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
#### マージ パブリケーションのアーティクルを定義する際の自動 ID 範囲管理を有効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 パブリッシュされているソース テーブルに id 列がある場合は、値を指定 **自動** の **@identityrangemanagementoption**, のサーバー サブスクリプションに割り当てられる id 値の範囲 **@pub_identity_range**, 、パブリッシャーとでは、各クライアント サブスクリプションに割り当てられる id 値の範囲 **@identity_range**, 、に対して新しい id 範囲が割り当てられる前に使用される合計 id 値の割合と **@threshold**します。 新しい id 範囲が割り当てられている場合の詳細についてに Id 範囲の割り当てを参照して [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。 詳細については、アーティクルを定義する、次を参照してください。 [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
    > [!NOTE]  
    >  特にサーバー サブスクリプションを使用するサブスクライバーの場合、ID 列のデータ型のサイズが、すべてのサブスクライバーに割り当てられる ID 範囲の総計をサポートできるだけの大きさであることを確認してください。  
  
#### マージ パブリケーションのアーティクルを定義する際に自動 ID 範囲管理を無効にするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 次のいずれかの値を **@identityrangemanagementoption**に指定します。  
  
    -   **手動** -サブスクライバーを更新するために、Id 範囲を手動で割り当てる必要があります。  
  
    -   **[なし]** -パブリッシャーの Id 列は、サブスクライバーで id 列としては定義されません。  
  
     詳細については、アーティクルを定義する、次を参照してください。 [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
2.  サブスクライバーの更新時に競合が発生しないように、サブスクライバーの ID アーティクル列に範囲を割り当てます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの既存のアーティクルに対する ID 範囲管理設定を自動的に変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md) の値をメモ **identityrangemanagementoption** 結果セットにします。 値が **0**の場合、自動 ID 範囲管理は有効ではありません。  
  
2.  結果セットの **identityrangemanagementoption** の値が **1**の場合、次のようにして設定を変更します。  
  
    -   割り当てられている id 範囲を変更するには実行 [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **identity_range** または **identity_range** の **@property** の新しい値の範囲と **@value**します。  
  
    -   新しい範囲の割り当てのしきい値を変更するには、実行 [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 **@property** に **threshold** を指定し、 **@value**に新しいしきい値を指定します。  
  
#### マージ パブリケーションの既存のアーティクルに対する ID 範囲管理設定を自動的に変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) の値をメモ **identity_support** 結果セットにします。 値が **0**の場合、自動 ID 範囲管理は有効ではありません。  
  
2.  場合の値 **identity_support** 結果セットが **1**, 、次のように設定を変更します。  
  
    -   割り当てられている id 範囲を変更するには実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **identity_range** または **identity_range** の **@property** の新しい値の範囲と **@value**します。  
  
    -   新しい範囲の割り当てのしきい値を変更するには、実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 **@property** に **threshold** を指定し、 **@value**に新しいしきい値を指定します。 新しい id 範囲が割り当てられている場合の詳細についてに Id 範囲の割り当てを参照して [Id 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)します。  
  
    -   自動 id 範囲管理を無効にするには実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 **@property** に **identityrangemanagementoption** を指定し、 **@value** に **manual** または **none**を指定します。  
  
## 参照  
 [ピア ツー ピア トランザクション レプリケーション](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [ID 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  