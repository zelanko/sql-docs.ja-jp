---
title: 並列データ ウェアハウスでのアクセス許可 |Microsoft ドキュメント
description: この記事では、要件と並列データ ウェアハウスのデータベース アクセス許可を管理するためのオプションについて説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 16ed81d3349cd1e641a66a95d9993e2a86ca4098
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="managing-permissions-in-parallel-data-warehouse"></a>Parallel Data Warehouse でのアクセス許可の管理
この記事では、要件と SQL Server PDW のデータベース アクセス許可を管理するためのオプションについて説明します。  
  
## <a name="BackupRestoreBasics"></a>データベース エンジンの権限の基本  
SQL Server PDW のデータベース エンジンの権限は、ログイン、サーバー レベルでは、データベース ユーザーとユーザー定義データベース ロール、データベース レベルで管理されます。  
  
**ログイン**  
ログインは、SQL Server PDW へのログオンの個々 のユーザー アカウントです。 SQL Server PDW では、Windows 認証と SQL Server 認証を使用してログインをサポートします。  Windows 認証のログインには、Windows ユーザーまたは SQL Server PDW で信頼されている任意のドメインからの Windows グループを指定できます。 SQL Server 認証のログインが定義され、SQL Server PDW によって認証され、パスワードを指定して作成する必要があります。  
  
メンバー、 **sysadmin**固定サーバー ロール (など、 **sa**ログイン) のデータベース ユーザーにマップされることがなく、データベースに接続できます。 割り当てられる、 **dbo**ユーザー。 データベースの所有者としてマップされても、 **dbo**ユーザー。  
  
**サーバーの役割**  
サーバー レベルの権限の便利なグループを提供する構成済みのロールのセットでの 4 つの特別なサーバー ロールがあります。 **Sysadmin**、 **MediumRC**、 **LargeRC**、および**XLargeRCfixed**サーバー ロールは、SQL で現在実装されている唯一のサーバー ロールServer PDW です。 **Sa**ログインは、唯一のメンバーでは、 **sysadmin**には、固定サーバー ロール、および追加のログインを追加することはできません、 **sysadmin**ロール。 ログインを与えることができる、 **CONTROL SERVER**は似ていますが、同一ではありませんに、アクセス許可、 **sysadmin**固定サーバー ロール。 使用して[ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)他のサーバー ロールにメンバーを追加します。 SQL Server PDW では、ユーザー定義サーバー ロールはサポートされていません。  
  
**データベース ユーザー**  
ログインは、データベースのデータベース ユーザーを作成して、そのデータベース ユーザー ログインをマッピングして、データベースへのアクセスが付与されます。 通常、データベース ユーザー名はログイン名と同じですが、同じにする必要はありません。 各データベース ユーザーは、単一のログインにマッピングされます。 ログインはデータベース内の 1 つのユーザーにのみマッピングできますが、異なる複数のデータベースにデータベース ユーザーとしてマッピングできます。  
  
**固定データベース ロール**  
固定データベース ロールでは、データベース レベルの権限の便利なグループを提供する構成済みのロールのセットです。 データベース ユーザーおよびユーザー定義データベース ロールを使用して固定データベース ロールに追加することができます、 [sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)プロシージャです。 固定データベース ロールの詳細については、次を参照してください。[固定データベース ロール](#fixed-database-roles)です。  
  
**ユーザー定義データベース ロール**  
持つユーザー、 **CREATE ROLE**権限は、一般的な権限を持つユーザーのグループを表すため、新しいデータベースのユーザー定義ロールを作成できます。 通常、権限の管理と監視を簡略化するために、権限はロール全体に対して付与または拒否されます。  
  
使用してセキュリティ プリンシパル (ログイン、ユーザー、およびロール) にアクセス許可が付与されます、 **GRANT**ステートメントです。 使用してアクセス許可を明示的に拒否、 **DENY**コマンド。 以前に付与または拒否された権限を削除するを使用して、**取り消す**ステートメントです。 権限は累積的であるため、ユーザーはユーザー、ログイン、すべてのグループ メンバーシップに付与された権限をすべて受け取ります。ただし、権限の拒否はすべての付与をオーバーライドします。 <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->  
  
次の例は、権限を構成する一般的な方法および推奨される方法を示します。  
  
1.  Windows 認証を使用する場合は、各 Windows ユーザーまたは SQL Server PDW に接続する Windows グループのログインを作成します。 SQL Server 認証を使用する場合は、SQL Server PDW に接続する各ユーザーに対してログインを作成します。  
  
2.  必要なすべてのデータベースのログインごとにデータベース ユーザーを作成します。  
  
3.  それぞれのような職務を表す 1 つまたは複数のユーザー定義データベース ロールを作成します。 たとえば、財務アナリストやセールス アナリストなどです。  
  
4.  データベース ユーザーを 1 つまたは複数のユーザー定義データベース ロールに追加します。  
  
5.  ユーザー定義データベース ロールに権限を付与します。  
  
ログインでサーバー レベルのオブジェクト、表示して一覧に表示する[sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)です。 サーバー プリンシパルには、サーバー レベルの権限のみを付与することができます。  
  
データベース レベルのオブジェクトは、ユーザーとデータベース ロール、および表示して一覧表示できます[sys.database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)です。 のみのデータベース プリンシパルをデータベース レベルのアクセス許可を付与できます。  
  
## <a name="BackupTypes"></a>既定のアクセス許可  
次の一覧には、既定のアクセス許可について説明します。  
  
-   Using してログインを作成するときに**CREATE LOGIN**ステートメントでは、ログインを受け取る、 **CONNECT SQL** SQL Server PDW に接続するログインを許可する権限です。  
  
-   使用して、データベース ユーザーを作成するときに、 **CREATE USER**ステートメントでは、ユーザーの受信、**ON DATABASE の接続:: * * * < database_name >* 権限、そのデータベースに接続するログインを許可します。ユーザーです。  
  
-   パブリックのロールを含む、すべてのプリンシパルない明示的または暗黙的なアクセス許可を持って既定では暗黙の権限は明示的なアクセス許可から継承されるためです。 そのため、明示的なアクセス許可が存在しない場合があることができますありません暗黙的なアクセス許可です。  
  
-   ログインには、オブジェクトまたはデータベースの所有者になると、ログインは常に、オブジェクトまたはデータベースに対するすべてのアクセス許可を持ちます。 所有者のアクセス許可は、明示的なアクセス許可として表示されません。 **GRANT**、**取り消す**、および**DENY**ステートメントは所有者のアクセス許可に影響を与えるありません。 使用して所有権を変更することができます、 [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md)ステートメントです。  
  
-   Sa ログインは、アプライアンスのすべてのアクセス許可を持っています。 所有者のアクセス許可と同様に、sa の権限は、変更することはできず、明示的なアクセス許可として表示されません。 **GRANT**、**取り消す**、および**DENY**ステートメントは sa のアクセス許可に影響を与えるありません。  
  
-   パブリック サーバーの役割は、既定ではアクセス許可を受信しないと、他のサーバー ロールからアクセス許可を継承していません。 PUBLIC サーバー ロールにより、明示的なアクセス許可を得ることができます、 **GRANT**、**取り消す**、および**DENY**ステートメントです。  
  
-   トランザクションでは、アクセス許可は必要ありません。 すべてのプリンシパルが実行できる、 **BEGIN TRANSACTION**、**コミット**、および**ロールバック**トランザクション コマンドです。 ただし、プリンシパルには、トランザクション内の各ステートメントを実行する適切なアクセス許可が必要です。  
  
-   **USE** ステートメントでは、権限は必要ありません。 すべてのプリンシパルが実行できる、**使用**で任意のデータベースでは、ステートメントが、データベースへのアクセスは、データベースのユーザー プリンシパルが必要か、guest ユーザーを有効にする必要があります。  
  
### <a name="the-public-role"></a>PUBLIC ロール  
アプライアンスのすべての新しいログインは、PUBLIC ロールに自動的に属しています。 PUBLIC サーバー ロールには、次の特徴があります。  
  
-   既定では、PUBLIC サーバー ロールのアクセス許可がありません。  
  
-   すべてのプリンシパル、PUBLIC サーバー ロールのメンバーであるし、PUBLIC サーバー ロールは、別のサーバー ロールのメンバーではありません。  
  
-   PUBLIC サーバー ロールには、暗黙的なアクセス許可を継承できません。 PUBLIC ロールに与えられている、権限を明示的に付与する必要があります。  
  
## <a name="BackupProc"></a>権限の決定  
ログインが、特定のアクションを実行するアクセス許可を持つかどうかは、ログイン、ユーザー、およびロールのメンバーであるユーザーに付与または拒否のアクセス許可によって異なります。 サーバー レベルの権限 (など**CREATE LOGIN**と**VIEW SERVER STATE**) サーバー レベルのプリンシパル (ログイン) を使用します。 データベース レベルのアクセス許可 (など**選択**テーブルからまたは**EXECUTE**プロシージャに対して) データベース レベルのプリンシパル (ユーザーとデータベース ロール) を使用します。  
  
### <a name="implicit-and-explicit-permissions"></a>暗黙的および明示的なアクセス許可  
*明示的なアクセス許可*は、**GRANT** または **DENY** ステートメントによってプリンシパルに付与される **GRANT** または **DENY** アクセス許可です。 データベース レベルの権限は、「、 [sys.database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)ビュー。 サーバー レベルの権限は、「、 [sys.server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)ビュー。  
  
*暗黙のアクセス許可*は、 **GRANT**または**DENY**プリンシパル (ログインまたはサーバー ロール) は、継承を許可します。 次の方法では、アクセス許可を継承できます。  
  
-   プリンシパルは、プリンシパル、プリンシパルは、明示的な持っていない場合でも、ロールのメンバーである場合に、ロールからのアクセス許可を継承できます**GRANT**または**DENY**権限です。  
  
-   プリンシパルは、プリンシパル オブジェクトの親スコープ (など、テーブルまたはデータベース全体のアクセス許可のスキーマ) のいずれかのアクセス許可を持っている場合、下位のオブジェクト (テーブルなど) に対する権限を継承できます。  
  
-   プリンシパルは、下位アクセス許可を含むアクセス許可のことで、権限を継承することができます。 たとえば、 **ALTER ANY USER**権限には、両方が含まれる、 **CREATE USER**と **ALTER ON USER:: * * *<name>* アクセス許可。  
  
### <a name="determining-permissions-when-performing-actions"></a>アクションを実行するときに権限の決定  
プリンシパルに割り当てるアクセス許可を確認するプロセスは複雑です。 複雑さは、プリンシパルは複数のロールのメンバーであることができ、そのロール階層内の複数のレベルから権限を渡すことができますので、暗黙的なアクセス許可を決定するときに発生します。  
  
次の一覧には、アクセス許可を決定するための一般的な規則について説明します。  
  
-   所有権は、アクセス許可を意味します。  
  
    オブジェクトの所有者は、オブジェクトのすべてのアクセス許可を持ちます。 同様に、データベース所有者がデータベースに対するすべての権限と、オブジェクトに対するすべての権限、データベースにします。 これらのアクセス許可を変更することはできません。  
  
-   サーバー ロールのメンバーシップの階層内の複数のレベルのアクセス許可を継承できます。  
  
    たとえば、次のような状況があるとします。  
  
    -   ログイン David PerfAnalysts のデータベース ロールのメンバーであります。  
  
    -   PerfAnalysts は、運用環境のデータベース ロールのメンバーです。  
  
    -   David と PerfAnalysts されていない**選択**Customer テーブルに対する権限。 アクセス許可が失効または明示的に付与します。  
  
    -   運用環境が**選択**Customer テーブルに対する権限。  
  
    この場合、PerfAnalysts が継承されます**GRANT**運用、および David から Customer テーブルに対する権限が継承されます**GRANT**実稼働からの Customer テーブルに対する権限。  
  
-   **DENY**オーバーライド**GRANT**アクセス許可が競合するとします。  
  
    たとえば、ログイン David 顧客テーブルにアクセス許可がない 2 つのデータベース ロールのメンバーであると – を持つ dbgroup1 **DENY**を持つ dbgroup2 と Customer テーブルに対する権限**GRANT**Customer テーブルに対する権限。 この例では、David が継承されます、 **DENY** Customer テーブルに対する権限。 これは、明示的または暗黙的に、ロールがそのアクセス許可を得られるかどうかの場合です。  
  
### <a name="auditing-permissions"></a>アクセス許可の監査  
ユーザーのチェック、次のアクセス許可を調査します。  
  
-   ログインがシステム管理者の判断には、次のクエリを実行します。  
  
    ```sql  
    SELECT SPLogins.name, 'is a member of ', SPRoles.name   
    FROM sys.server_role_members AS SRM   
    JOIN sys.server_principals AS SPRoles   
        ON SRM.role_principal_id = SPRoles.principal_id   
    JOIN sys.server_principals AS SPLogins   
        ON SRM.member_principal_id = SPLogins.principal_id;  
    ```  
  
-   明示的な権限がログインに付与されてを決定する次のクエリを実行します。  
  
    ```sql  
    SELECT name, 'has the ', state_desc , permission_name, ' permission'  
    FROM sys.server_permissions AS SP  
    JOIN sys.server_principals AS SPRoles   
        ON SP.grantee_principal_id = SPRoles.principal_id;  
    ```  
  
-   データベース ユーザーがデータベース ロールのメンバーであるかを決定するユーザー データベースで次のクエリを実行します。  
  
    ```sql  
    SELECT DPUsers.name, 'is a member of ', DPRoles.name    
    FROM sys.database_role_members AS DRM  
    JOIN sys.database_principals AS DPRoles   
        ON DRM.role_principal_id = DPRoles.principal_id  
    JOIN sys.database_principals AS DPUsers  
        ON DRM.member_principal_id = DPUsers.principal_id;  
    ```  
  
-   データベース ユーザーおよびロールが許可または拒否された特定のアクセス許可を決定するユーザー データベースで次のクエリを実行します。 Sys.objects と sys.schemas、major_id で説明されている項目を識別するなどその他のビューをクエリする必要があります。  
  
    ```sql  
    SELECT DPUsers.name, 'has the ', permission_name,   
    'permission on the item described as class = ', class, 'id = ', major_id  
    FROM sys.database_permissions AS DP  
    JOIN sys.database_principals AS DPUsers  
        ON DP.grantee_principal_id = DPUsers.principal_id;  
    ```  
  
## <a name="RestoreProc"></a>データベースのアクセス許可のベスト プラクティス  
  
-   実用的では、最も詳細なレベルのアクセス許可を付与します。 権限を付与する、テーブルまたはビュー レベルの権限は、管理できなくなる可能性があります。 データベース レベルの権限を付与するのも行ってすぎる可能性があります。 作業境界を定義するスキーマを持つデータベースを設計すると、スキーマ権限の付与は、テーブル レベルとデータベース レベルの間の適切なセキュリティ侵害はおそらくです。  
  
-   ユーザーまたはログインではなく、ロールへのアクセス許可を付与します。 ユーザーではなくロールを使用して権限を管理しやすい迅速に許可またはロールの内外に移動してユーザーまたはログインに対する権限のセットを取り消します。 関数が 1 人のユーザーからに渡すとき別、アクセス許可がロールのメンバーシップの変更中に、ロール レベルでにそのまま残ります。  
  
-   ジョブ機能と、操作を実行する会社のグループに基づくジョブ関数の役割を結合する上位レベルのグループの役割に基づいてロールに権限を付与します。  
  
-   すべてのエンド ユーザー固有のログインが必要です。 ログインを共有するユーザーを許可しません。 各ユーザーのログインを提供することにより、監査証跡し、アクセス許可の管理が簡単になります。  
  
## <a name="fixed-database-roles"></a>固定データベース ロール
SQL Server では、サーバーに対する権限を管理するために (固定) データベース レベルのロールを事前に構成を提供します。 割り当てられているアクセス許可を変更することはできませんが、構成済みのロールは固定です。 ユーザー定義データベース ロールを作成することもできます。 ユーザー定義データベース ロールに割り当てられたアクセス許可を変更することができます。  
  
ロールは、その他のプリンシパルをグループ化するセキュリティ プリンシパルです。 データベース ロールは、データベース全体のアクセス許可のスコープ内です。 データベース ユーザーとその他のデータベース ロールは、データベース ロールのメンバーとして追加できます。 固定データベース ロールは、互いに追加できません。 (*ロール* は、Windows オペレーティング システムの *グループ* に似ています)。  
  
9 の固定データベース ロールがあります。  
  
-   **db_owner**  
  
-   **db_securityadmin**  
  
-   **db_accessadmin**  
  
-   **db_backupoperator**  
  
-   **db_ddladmin**  
  
-   **db_datawriter**  
  
-   **db_datareader**  
  
-   **db_denydatawriter**  
  
-   **db_denydatareader**  
  
### <a name="permissions-of-the-fixed-database-roles"></a>固定データベース ロールの権限  
固定サーバー ロールおよび固定データベース ロールのシステムは、1980 で生成されたレガシ システムです。 固定ロールでは、サポートされていて、数名のユーザーが、セキュリティ ニーズがシンプルかつ環境で便利です。 SQL Server 2005 以降では、権限の許可の詳細なシステムが作成されました。 この新しいシステムはより詳細な許可と権限の拒否の両方の多数のオプションを提供することです。 詳細なシステムの特別な複雑さが困難になりますについてが、ほとんどのエンタープライズ システムは、固定ロールを使用する代わりにアクセス許可を付与する必要があります。 <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->次の表は、各固定データベース ロールに関連付けられている権限を示しています。 この SQL Server グラフィックにすべてのアクセス許可が使用可能な (または必要に応じて) AP でします。  
  
![APS セキュリティの固定データベース ロール](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")  
  
### <a name="related-content"></a>関連コンテンツ  
  
-   ユーザー定義ロールを作成するを参照してください。 [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)です。  
  
  
## <a name="fixed-server-roles"></a>固定サーバー ロール
固定サーバー ロールは、SQL Server によって自動的に作成されます。 SQL Server PDW では、SQL Server 固定サーバー ロールの制限の実装があります。 のみ、 **sysadmin**と**パブリック**メンバーとしてユーザー ログインがあります。 **Setupadmin**と**dbcreator**ロールは、SQL Server PDW によって内部的に使用されます。 追加のメンバーを追加または任意のロールから削除できません。  
  
### <a name="sysadmin-fixed-server-role"></a>sysadmin 固定サーバー ロール  
**sysadmin** 固定サーバー ロールのメンバーは、サーバーに対するすべての操作を実行できます。 **Sa**ログインは、唯一のメンバーでは、 **sysadmin**固定サーバー ロール。 追加のログインを追加することはできません、 **sysadmin**固定サーバー ロール。 **CONTROL SERVER** アクセス許可を付与すると、**sysadmin** 固定サーバー ロールのメンバーシップが概算されます。 次の例、 **CONTROL SERVER**ログインに権限が Fay をという名前です。  
  
```sql  
USE master;  
GO  
GRANT CONTROL SERVER TO Fay;  
```  
  
> [!IMPORTANT]  
> **CONTROL SERVER**権限が SQL Server PDW のほぼ完全に制御を提供します。 可能な限り、ログインをより詳細なアクセス許可を提供します。 たとえば、付与、 **VIEW SERVER STATE**、 **ALTER ANY LOGIN**、 **VIEW ANY DATABASE**、または**CREATE ANY DATABASE**アクセス許可です。  
  
### <a name="public-server-role"></a>public サーバー ロール  
ログインは SQL Server PDW に接続できる、すべてのメンバーである、**パブリック**サーバーの役割です。 すべてのログインに付与された権限の継承**パブリック**任意のオブジェクトにします。 のみを割り当てる**パブリック**オブジェクトのすべてのユーザーに利用を許可するときにオブジェクトに対する権限。 メンバーシップを変更することはできません、**パブリック**ロール。  
  
> [!NOTE]  
> **パブリック**は他のロールとは異なる実装します。 すべてのサーバー プリンシパルのメンバーシップ、public のメンバーであるため、**パブリック**ロールが記載されていない、 **sys.server_role_members** DMV。  
  
### <a name="fixed-server-roles-vs-granting-permissions"></a>固定サーバー ロールとします。権限を付与します。  
固定サーバー ロールおよび固定データベース ロールのシステムは、1980 で生成されたレガシ システムです。 固定ロールでは、サポートされていて、数名のユーザーが、セキュリティ ニーズがシンプルかつ環境で便利です。 SQL Server 2005 以降では、権限の許可の詳細なシステムが作成されました。 この新しいシステムはより詳細な許可と権限の拒否の両方の多数のオプションを提供することです。 詳細なシステムの特別な複雑さが困難になりますについてが、ほとんどのエンタープライズ システムは、固定ロールを使用する代わりにアクセス許可を付与する必要があります。 <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->  
  
## <a name="related-topics"></a>関連項目  
  
- [権限の許可](grant-permissions.md)

<!-- MISSING LINKS
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->

