---
title: SQL Server エージェントの固定データベース ロール | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, roles
- SQLAgentUserRole database role
- SQLAgentReaderRole database role
- multiple roles
- security [SQL Server Agent], fixed database roles
- fixed database roles [SQL Server]
- SQLAgentOperatorRole database role
ms.assetid: 719ce56b-d6b2-414a-88a8-f43b725ebc79
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a8067aaa2133648c1a1ea4fff81db08c139d5278
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67793402"
---
# <a name="sql-server-agent-fixed-database-roles"></a>SQL Server エージェントの固定データベース ロール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、次の**msdb**データベース固定データベースロールがあります。これにより[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、管理者はエージェントへのアクセスを細かく制御できます。 特権レベルの低いロールから順に、次に示します。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 上記のどのロールのメンバーでもないユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に接続しても、オブジェクト エクスプローラーには **[SQL Server エージェント]** ノードは表示されません。 
  ** エージェントを使用するユーザーは、上記のいずれかの固定データベース ロールのメンバーであるか、または固定サーバー ロール **sysadmin[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメンバーである必要があります。  
  
## <a name="permissions-of-sql-server-agent-fixed-database-roles"></a>SQL Server エージェントの固定データベース ロールの権限  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのデータベース ロールの各権限の相互関係は、同心構造になっています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント オブジェクト (警告、オペレーター、ジョブ、スケジュール、プロキシなど) に対して、高いレベルの特権を持つロールは、低いレベルの特権を持つロールの権限を継承します。 たとえば、最も特権レベルの低い **SQLAgentUserRole** のメンバーが proxy_A へのアクセスを許可された場合、 **SQLAgentReaderRole** および **SQLAgentOperatorRole** の両方のメンバーは、proxy_A へのアクセスが明示的に許可されていなくても、このプロキシへのアクセス権が自動的に与えられていることになります。 これは、セキュリティに影響することがあります。セキュリティ上の影響については、次のセクションの各ロールの説明に記載します。  
  
### <a name="sqlagentuserrole-permissions"></a>SQLAgentUserRole の権限  
 **SQLAgentUserRole**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの固定データベースロールの最小特権です。 オペレーター、ローカル ジョブ、ジョブ スケジュールのみに対する権限があります。 
  **SQLAgentUserRole** のメンバーは、所有しているローカル ジョブおよびジョブ スケジュールのみに対する権限を持っています。 このメンバーが、マルチサーバー ジョブ (マスター サーバーとターゲット サーバーのジョブ) を使用することはできません。また、ジョブの所有権を変更して、所有していないジョブへのアクセス権を得ることもできません。 **SQLAgentUserRole**のメンバーは、の [**ジョブステップ**の[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]プロパティ] ダイアログボックスでのみ、使用可能なプロキシの一覧を表示できます。 
  **SQLAgentUserRole** のメンバーに対しては、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーには **[ジョブ]** ノードだけが表示されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントデータベースロール**のメンバーにプロキシアクセスを許可する前に **、セキュリティ**への影響を考慮してください。 
  **SQLAgentReaderRole** および **SQLAgentOperatorRole** は、自動的に **SQLAgentUserRole**のメンバーになります。 つまり、 **SQLAgentReaderRole** および **SQLAgentOperatorRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLAgentUserRole** に許可されたすべての ** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
 次の表に、 ** エージェント オブジェクトに対する **SQLAgentUserRole[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の権限の概要を示します。  
  
|アクション|オペレーター|ローカル ジョブ<br /><br /> (所有しているジョブのみ)|ジョブ スケジュール<br /><br /> (所有しているスケジュールのみ)|プロキシ|  
|------------|---------------|----------------------------------------|------------------------------------------------|-------------|  
|作成/変更/削除|いいえ|はい <sup>1</sup>|はい|いいえ|  
|リストの表示 (列挙)|はい <sup>2</sup>|はい|はい|はい <sup>3</sup>|  
|有効化/無効化|いいえ|はい|はい|適用不可|  
|プロパティの表示|いいえ|はい|はい|いいえ|  
|実行/停止/開始|適用不可|はい|適用不可|適用不可|  
|ジョブ履歴の表示|適用不可|はい|適用不可|適用不可|  
|ジョブ履歴の削除|適用不可|いいえ <sup>4</sup>|適用不可|適用不可|  
|アタッチ/デタッチ|適用不可|適用不可|はい|適用不可|  
  
 <sup>1</sup>ジョブの所有権を変更することはできません。  
  
 <sup>2</sup> **sp_notify_operator**および Management Studio の [**ジョブのプロパティ**] ダイアログボックスで使用可能な演算子の一覧を取得できます。  
  
 <sup>3</sup> Management Studio の [**ジョブステップのプロパティ**] ダイアログボックスでのみ使用できるプロキシの一覧。  
  
 <sup>4</sup>所有しているジョブのジョブ履歴を削除するには、 **SQLAgentUserRole**のメンバーに対して、 **sp_purge_jobhistory**に対する EXECUTE 権限が明示的に許可されている必要があります。 他のジョブのジョブ履歴は削除できません。  
  
### <a name="sqlagentreaderrole-permissions"></a>SQLAgentReaderRole の権限  
 **SQLAgentReaderRole**には、すべての**SQLAgentUserRole**権限だけでなく、使用できるマルチサーバージョブの一覧、そのプロパティ、およびそれらの履歴を表示する権限が含まれています。 このロールのメンバーは、所有しているジョブとジョブ スケジュールだけでなく、使用できるすべてのジョブとジョブ スケジュール、およびそのプロパティのリストを表示することもできます。 **SQLAgentReaderRole**メンバーは、ジョブの所有権を変更して、まだ所有していないジョブにアクセスすることはできません。 
  **SQLAgentReaderRole** のメンバーに対しては、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーには **[ジョブ]** ノードだけが表示されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントデータベースロール**のメンバーにプロキシアクセスを許可する前に **、セキュリティ**への影響を考慮してください。 
  **SQLAgentReaderRole** のメンバーは、自動的に **SQLAgentUserRole**のメンバーになります。 つまり、 **SQLAgentReaderRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLAgentUserRole** に対して許可されたすべての ** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
 次の表に、 ** エージェント オブジェクトに対する **SQLAgentReaderRole[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の権限の概要を示します。  
  
|アクション|オペレーター|ローカル ジョブ|マルチサーバー ジョブ|ジョブ スケジュール|プロキシ|  
|------------|---------------|----------------|----------------------|-------------------|-------------|  
|作成/変更/削除|いいえ|可<sup>1</sup> (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|リストの表示 (列挙)|はい <sup>2</sup>|はい|はい|はい|はい <sup>3</sup>|  
|有効化/無効化|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|適用不可|  
|プロパティの表示|いいえ|はい|はい|はい|いいえ|  
|プロパティの編集|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|実行/停止/開始|適用不可|可 (所有しているジョブのみ)|いいえ|適用不可|適用不可|  
|ジョブ履歴の表示|適用不可|はい|はい|適用不可|適用不可|  
|ジョブ履歴の削除|適用不可|いいえ <sup>4</sup>|いいえ|適用不可|適用不可|  
|アタッチ/デタッチ|適用不可|適用不可|適用不可|可 (所有しているスケジュールのみ)|適用不可|  
  
 <sup>1</sup>ジョブの所有権を変更することはできません。  
  
 <sup>2</sup> **sp_notify_operator**および Management Studio の [**ジョブのプロパティ**] ダイアログボックスで使用可能な演算子の一覧を取得できます。  
  
 <sup>3</sup> Management Studio の [**ジョブステップのプロパティ**] ダイアログボックスでのみ使用できるプロキシの一覧。  
  
 <sup>4</sup>所有しているジョブのジョブ履歴を削除するには、 **SQLAgentReaderRole**のメンバーに対して、 **sp_purge_jobhistory**に対する EXECUTE 権限が明示的に許可されている必要があります。 他のジョブのジョブ履歴は削除できません。  
  
### <a name="sqlagentoperatorrole-permissions"></a>SQLAgentOperatorRole の権限  
 **Sqlagentoperatorrole**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの固定データベースロールの中で最も特権が高い権限です。 これには、 **SQLAgentUserRole** および **SQLAgentReaderRole**のすべての権限が含まれています。 このロールのメンバーは、オペレーターおよびプロキシのプロパティを表示することも、サーバー上で使用できるプロキシおよび警告を列挙することもできます。  
  
 **Sqlagentoperatorrole**のメンバーは、ローカルジョブおよびスケジュールに対する追加の権限を持っています。 すべてのローカル ジョブを実行、停止、または開始したり、サーバー上のローカル ジョブのジョブ履歴を削除できます。 また、サーバー上のすべてのローカル ジョブおよびスケジュールを、有効または無効にすることもできます。 ローカル ジョブまたはスケジュールを有効または無効にするには、このロールのメンバーはストアド プロシージャ **sp_update_job** および **sp_update_schedule**を使用する必要があります。 **Sqlagentoperatorrole**のメンバーは、ジョブまたはスケジュールの名前または識別子と** \@有効な**パラメーターを指定するパラメーターのみを指定できます。 他のパラメーターを指定すると、ストアド プロシージャの実行は失敗します。 **Sqlagentoperatorrole**のメンバーは、ジョブの所有権を変更して、まだ所有していないジョブにアクセスすることはできません。  
  
 
  **SQLAgentOperatorRole**のメンバーに対しては、 **オブジェクト エクスプローラーには**[ジョブ] **ノード、**[警告] **ノード、** [オペレーター] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ノード、および **[プロキシ]** ノードのみが表示されます。 このロールのメンバーに表示されないのは、 **[エラー ログ]** ノードだけです。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントデータベースロール**のメンバーにプロキシアクセスを許可する前に **、セキュリティ**への影響を考慮してください。 
  **SQLAgentOperatorRole** のメンバーは、自動的に **SQLAgentUserRole** および **SQLAgentReaderRole**のメンバーになります。 つまり、 **SQLAgentOperatorRole** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQLAgentUserRole** または **SQLAgentReaderRole** に対して許可されたすべての ** エージェント プロキシにアクセスし、これらのプロキシを使用できることになります。  
  
 次の表に、 **エージェント オブジェクトに対する** SQLAgentOperatorRole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の権限の概要を示します。  
  
|アクション|警告|オペレーター|ローカル ジョブ|マルチサーバー ジョブ|ジョブ スケジュール|プロキシ|  
|------------|------------|---------------|----------------|----------------------|-------------------|-------------|  
|作成/変更/削除|いいえ|いいえ|可<sup>2</sup> (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|リストの表示 (列挙)|はい|はい <sup>1</sup>|はい|はい|はい|はい|  
|有効化/無効化|いいえ|いいえ|はい <sup>3</sup>|いいえ|はい <sup>4</sup>|適用不可|  
|プロパティの表示|はい|はい|はい|はい|はい|はい|  
|プロパティの編集|いいえ|いいえ|可 (所有しているジョブのみ)|いいえ|可 (所有しているスケジュールのみ)|いいえ|  
|実行/停止/開始|適用不可|適用不可|はい|いいえ|適用不可|適用不可|  
|ジョブ履歴の表示|適用不可|適用不可|はい|はい|適用不可|適用不可|  
|ジョブ履歴の削除|適用不可|適用不可|はい|いいえ|適用不可|適用不可|  
|アタッチ/デタッチ|適用不可|適用不可|適用不可|適用不可|可 (所有しているスケジュールのみ)|適用不可|  
  
 <sup>1</sup> **sp_notify_operator**および Management Studio の [**ジョブのプロパティ**] ダイアログボックスで使用可能な演算子の一覧を取得できます。  
  
 <sup>2</sup>ジョブの所有権を変更することはできません。  
  
 <sup>3</sup> **sqlagentoperatorrole**のメンバーは、ストアドプロシージャ**sp_update_job**を使用し、 ** \@enabled**パラメーターと** \@job_id** (または** \@job_name**) パラメーターの値を指定することにより、所有していないローカルジョブを有効または無効にすることができます。 このロールのメンバーが、このストアド プロシージャに対して他のパラメーターを指定した場合、プロシージャの実行は失敗します。  
  
 <sup>4</sup> **sqlagentoperatorrole**のメンバーは、ストアドプロシージャ**sp_update_schedule**を使用し、 ** \@enabled**パラメーターと** \@schedule_id** (または** \@name**) パラメーターの値を指定することによって、所有していないスケジュールを有効または無効にすることができます。 このロールのメンバーが、このストアド プロシージャに対して他のパラメーターを指定した場合、プロシージャの実行は失敗します。  
  
## <a name="assigning-users-multiple-roles"></a>ユーザーへの複数のロールの割り当て  
 固定サーバー ロール **sysadmin** のメンバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのすべての機能にアクセスできます。 
  **sysadmin** ロールのメンバーではないが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの複数の固定データベース ロールのメンバーであるユーザーの場合、これらのロールの同心構造権限モデルについて覚えておくことが重要です。 特権レベルの高いロールには常に、そのロールよりも特権レベルが低いロールの権限がすべて含まれているため、複数のロールのメンバーであるユーザーは、そのユーザーがメンバーとして属しているロールの中で、最も特権レベルの高いロールに関連付けられた権限を自動的に持っていることになります。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントセキュリティを実装する](implement-sql-server-agent-security.md)   
 [sp_update_job &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)   
 [sp_update_schedule &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)   
 [sp_notify_operator &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)   
 [sp_purge_jobhistory &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)  
  
  
