---
title: Parallel Data Warehouse でのアクセス許可 |Microsoft Docs
description: この記事では、要件および Parallel Data Warehouse のデータベース アクセス許可を管理するためのオプションについて説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2284c6b39693363de262e4ea307b0de45a0b6f06
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960398"
---
# <a name="managing-permissions-in-parallel-data-warehouse"></a>Parallel Data Warehouse でのアクセス許可の管理
この記事では、要件および SQL Server PDW のデータベース アクセス許可を管理するためのオプションについて説明します。  
  
## <a name="BackupRestoreBasics"></a>データベース エンジンのアクセス許可の基本  
SQL Server PDW のデータベース エンジンの権限は、ログイン、を介してサーバー レベルおよびデータベース ユーザーおよびユーザー定義データベース ロールを介して、データベース レベルで管理されます。  
  
**ログイン**  
ログインは、SQL Server の PDW へのログオンの個々 のユーザー アカウントです。 SQL Server PDW では、Windows 認証と SQL Server 認証を使用してログインをサポートします。  Windows 認証ログインには、Windows ユーザーまたは SQL Server PDW で信頼されている任意のドメインからの Windows グループを指定できます。 SQL Server 認証ログインが定義され、SQL Server PDW によって認証され、パスワードを指定して作成する必要があります。  
  
メンバー、 **sysadmin**固定サーバー ロール (など、 **sa**ログイン) のデータベース ユーザーにマップされることがなく、データベースに接続できます。 割り当てられる、 **dbo**ユーザー。 データベースの所有者としてマップも、 **dbo**ユーザー。  
  
**サーバーの役割**  
一連のサーバー レベル権限の便利なグループを提供する事前構成済みのロールの 4 つの特別なサーバー ロールがあります。 **Sysadmin**、 **MediumRC**、 **LargeRC**、および**XLargeRCfixed**サーバー ロールは、SQL で現在実装されている唯一のサーバー ロールPDW のサーバー。 **Sa**ログインが唯一のメンバー、 **sysadmin**に固定サーバー ロール、および追加のログインを追加できません、 **sysadmin**ロール。 ログインを与えることができる、 **CONTROL SERVER**同一ではありませんには同様で、このアクセス許可、 **sysadmin**固定サーバー ロール。 使用[ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)他のサーバー ロールにメンバーを追加します。 SQL Server PDW は、ユーザー定義サーバー ロールをサポートしていません。  
  
**データベース ユーザー**  
ログインは、データベースのデータベース ユーザーを作成して、そのデータベースのユーザーをログインにマッピングで、データベースへのアクセスが付与されます。 通常、データベース ユーザー名はログイン名と同じですが、同じにする必要はありません。 各データベース ユーザーは、単一のログインにマッピングされます。 ログインはデータベース内の 1 つのユーザーにのみマッピングできますが、異なる複数のデータベースにデータベース ユーザーとしてマッピングできます。  
  
**固定データベース ロール**  
固定データベース ロールでは、データベース レベルの権限の便利なグループを提供する事前構成済みのロールのセットです。 使用して固定データベース ロールには、データベース ユーザーおよびユーザー定義データベース ロールを追加することができます、 [sp_addrolemember](../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)プロシージャ。 固定データベース ロールの詳細については、次を参照してください。[の固定データベース ロール](#fixed-database-roles)します。  
  
**ユーザー定義データベース ロール**  
持つユーザー、 **CREATE ROLE**アクセス許可は、一般的な権限を持つユーザーのグループを表すための新しいユーザー定義データベース ロールを作成できます。 通常、権限の管理と監視を簡略化するために、権限はロール全体に対して付与または拒否されます。  
  
使用してセキュリティ プリンシパル (ログイン、ユーザー、およびロール) にアクセス許可が付与されます、 **GRANT**ステートメント。 使用してアクセス許可を明示的に拒否、 **DENY**コマンド。 使用して、以前に付与または拒否された権限が削除された、**取り消す**ステートメント。 権限は累積的であるため、ユーザーはユーザー、ログイン、すべてのグループ メンバーシップに付与された権限をすべて受け取ります。ただし、権限の拒否はすべての付与をオーバーライドします。 <!-- MISSING LINKS (For information, syntax, and available permissions with these commands, see [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md)).  -->  
  
次の例は、権限を構成する一般的な方法および推奨される方法を示します。  
  
1.  Windows 認証を使用する場合は、各 Windows ユーザーまたは SQL Server PDW に接続する Windows グループのログインを作成します。 SQL Server 認証を使用する場合は、SQL Server PDW に接続する各ユーザーに対して、ログインを作成します。  
  
2.  必要なすべてのデータベースでは、ログインごとにデータベース ユーザーを作成します。  
  
3.  それぞれのような関数を表す 1 つまたは複数のユーザー定義データベース ロールを作成します。 たとえば、財務アナリストやセールス アナリストなどです。  
  
4.  データベース ユーザーを 1 つまたは複数のユーザー定義データベース ロールに追加します。  
  
5.  ユーザー定義データベース ロールに権限を付与します。  
  
ログインはサーバー レベル オブジェクトと、表示して一覧を表示できます[sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)します。 サーバー プリンシパルには、サーバー レベルのアクセス許可のみを付与することができます。  
  
データベース レベルのオブジェクトは、ユーザーとデータベース ロールを一覧表示できます[sys.database_principals](../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)します。 のみデータベース レベルのアクセス許可は、データベース プリンシパルに付与することができます。  
  
## <a name="BackupTypes"></a>既定のアクセス許可  
次の一覧には、既定のアクセス許可について説明します。  
  
-   Using してログインを作成するときに**CREATE LOGIN**ステートメントでは、ログインを受け取る、 **CONNECT SQL** SQL Server PDW に接続するログインを許可する権限。  
  
-   使用してデータベース ユーザーを作成するときに、 **CREATE USER**ステートメントでは、ユーザーの受信、 **ON DATABASE の接続::** _< database_name >_ アクセス許可、許可、ユーザーとしてそのデータベースへの接続にログインします。  
  
-   パブリックのロールを含む、すべてのプリンシパルない明示的または暗黙的なアクセス許可を持って既定では暗黙の権限は明示的なアクセス許可から継承されるためです。 そのため、明示的なアクセス許可が存在しない場合がありますはもできません暗黙的なアクセス許可です。  
  
-   ログインには、オブジェクトまたはデータベースの所有者になると、ログインは常に、オブジェクトまたはデータベースに対するすべてのアクセス許可を持ちます。 所有者のアクセス許可では、明示的なアクセス許可として表示されません。 **GRANT**、**取り消す**、および**DENY**所有者のアクセス許可にステートメントの影響がありません。 使用して所有権を変更することができます、 [ALTER AUTHORIZATION](../t-sql/statements/alter-authorization-transact-sql.md)ステートメント。  
  
-   Sa ログインは、アプライアンスのすべてのアクセス許可を持ちます。 所有者のアクセス許可と同様に、sa 権限は、変更することはできず、明示的なアクセス許可として表示されません。 **GRANT**、**取り消す**、および**DENY**に sa 権限ステートメントの影響がありません。  
  
-   PUBLIC サーバー ロールは、既定のアクセス許可を受信しないと、他のサーバー ロールからアクセス許可を継承していません。 PUBLIC サーバー ロールに明示的なアクセス許可を与えることが、 **GRANT**、**取り消す**、および**DENY**ステートメント。  
  
-   トランザクションでは、アクセス許可は必要ありません。 すべてのプリンシパルが実行できる、 **BEGIN TRANSACTION**、**コミット**、および**ロールバック**トランザクション コマンドです。 ただし、プリンシパルには、トランザクション内の各ステートメントを実行する適切なアクセス許可が必要です。  
  
-   **USE** ステートメントでは、権限は必要ありません。 すべてのプリンシパルが実行できる、**使用**ステートメントで任意のデータベースにアクセスするデータベースは、データベースのユーザー プリンシパルが必要か、ゲスト ユーザーを有効にする必要があります。  
  
### <a name="the-public-role"></a>PUBLIC ロール  
すべての新しいアプライアンス ログインは PUBLIC ロールに自動的に属しています。 PUBLIC サーバー ロールには、次の特徴があります。  
  
-   既定では、PUBLIC サーバー ロールのアクセス許可がありません。  
  
-   すべてのプリンシパル、PUBLIC サーバー ロールのメンバーであるし、PUBLIC サーバー ロールが別のサーバー ロールのメンバーではありません。  
  
-   PUBLIC サーバー ロールには、暗黙的なアクセス許可を継承できません。 PUBLIC ロールに与えられたアクセス許可を明示的に付与する必要があります。  
  
## <a name="BackupProc"></a>アクセス許可の決定  
ログインが、特定のアクションを実行するアクセス許可を持つかどうかは、ログイン、ユーザー、およびロールのメンバーであるユーザーに付与または拒否のアクセス許可によって異なります。 サーバー レベルの権限 (など**CREATE LOGIN**と**VIEW SERVER STATE**) サーバー レベル プリンシパル (ログイン) を利用できます。 データベース レベルのアクセス許可 (など**選択**テーブルからまたは**EXECUTE**プロシージャに) データベース レベルのプリンシパル (ユーザーとデータベース ロール) を利用できます。  
  
### <a name="implicit-and-explicit-permissions"></a>暗黙的および明示的なアクセス許可  
*明示的なアクセス許可*は、**GRANT** または **DENY** ステートメントによってプリンシパルに付与される **GRANT** または **DENY** アクセス許可です。 データベース レベルのアクセス許可が記載されて、 [sys.database_permissions](../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)ビュー。 サーバー レベルのアクセス許可が記載されて、 [sys.server_permissions](../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)ビュー。  
  
*暗黙のアクセス許可*は、 **GRANT**または**DENY**プリンシパル (ログインまたはサーバー ロール) は、継承したアクセス許可。 次の方法では、アクセス許可を継承できます。  
  
-   プリンシパルは、プリンシパルを明示的にすることはない場合でも、プリンシパル、ロールのメンバーである場合に、ロールからのアクセス許可を継承できます**GRANT**または**DENY**権限。  
  
-   プリンシパルは、プリンシパル オブジェクトの親スコープ (など、テーブルまたはデータベース全体のアクセス許可のスキーマ) のいずれかでアクセス許可を持っている場合 (テーブル) などの下位のオブジェクトに対する権限を継承できます。  
  
-   プリンシパルは、下位のアクセス許可を含むアクセス許可を持つ、アクセス許可を継承できます。 たとえば、 **ALTER ANY USER**両方のアクセス許可が含まれています、 **CREATE USER**と**ALTER ON USER::** _<name>_ アクセス許可。  
  
### <a name="determining-permissions-when-performing-actions"></a>アクションを実行するときに、アクセス許可の決定  
プリンシパルに割り当てるアクセス許可を決定するプロセスは複雑です。 複雑さは、プリンシパルは複数のロールのメンバーであることができ、そのロール階層内の複数のレベルでアクセス許可を渡すことができますので、暗黙的なアクセス許可を決定するときに発生します。  
  
次の一覧には、アクセス許可を決定するための一般的な規則について説明します。  
  
-   所有権は、アクセス許可を意味します。  
  
    オブジェクトの所有者は、オブジェクトのすべてのアクセス許可を持ちます。 同様に、データベース所有者が、データベースに対するすべての権限とオブジェクトのすべてのアクセス許可、データベースでします。 これらのアクセス許可を変更できません。  
  
-   サーバー ロールのメンバーシップの階層内の複数のレベルのアクセス許可を継承できます。  
  
    たとえば、次のような状況があるとします。  
  
    -   ログインの David PerfAnalysts のデータベース ロールのメンバーであります。  
  
    -   PerfAnalysts は、運用環境のデータベース ロールのメンバーです。  
  
    -   David と PerfAnalysts されていない**選択**Customer テーブルに対する権限。 アクセス許可が失効かしたり明示的に付与します。  
  
    -   運用環境が**選択**Customer テーブルに対する権限。  
  
    PerfAnalysts がここでは、継承は**GRANT**は、運用環境と David から Customer テーブルに対する権限を継承**GRANT**運用から Customer テーブルに対する権限。  
  
-   **DENY**オーバーライド**GRANT**アクセス許可が競合するとき。  
  
    たとえば、ログイン David 顧客テーブルにアクセス許可がない 2 つのデータベース ロールのメンバーであると -dbgroup1 が**DENY** Customer テーブルとのある、dbgroup2 に対する権限**GRANT**Customer テーブルに対する権限。 この場合は、David は継承、 **DENY** Customer テーブルに対する権限。 これは、明示的または暗黙的に、ロールがそのアクセス許可を得られるかどうかの場合です。  
  
### <a name="auditing-permissions"></a>アクセス許可を監査  
ユーザーのチェック、次のアクセス許可を調査します。  
  
-   ログインがシステム管理者であるかを確認する次のクエリを実行します。  
  
    ```sql  
    SELECT SPLogins.name, 'is a member of ', SPRoles.name   
    FROM sys.server_role_members AS SRM   
    JOIN sys.server_principals AS SPRoles   
        ON SRM.role_principal_id = SPRoles.principal_id   
    JOIN sys.server_principals AS SPLogins   
        ON SRM.member_principal_id = SPLogins.principal_id;  
    ```  
  
-   ログインには明示的なアクセス許可が付与されているかを判断する次のクエリを実行します。  
  
    ```sql  
    SELECT name, 'has the ', state_desc , permission_name, ' permission'  
    FROM sys.server_permissions AS SP  
    JOIN sys.server_principals AS SPRoles   
        ON SP.grantee_principal_id = SPRoles.principal_id;  
    ```  
  
-   データベース ユーザーがデータベース ロールのメンバーであるかを決定するユーザー データベースでは、次のクエリを実行します。  
  
    ```sql  
    SELECT DPUsers.name, 'is a member of ', DPRoles.name    
    FROM sys.database_role_members AS DRM  
    JOIN sys.database_principals AS DPRoles   
        ON DRM.role_principal_id = DPRoles.principal_id  
    JOIN sys.database_principals AS DPUsers  
        ON DRM.member_principal_id = DPUsers.principal_id;  
    ```  
  
-   データベース ユーザーおよびロールが許可または特定のアクセス許可が拒否されているを確認するユーザー データベースでは、次のクエリを実行します。 Sys.objects と sys.schemas、major_id で説明されている項目を識別するなどの追加のビューをクエリする必要があります。  
  
    ```sql  
    SELECT DPUsers.name, 'has the ', permission_name,   
    'permission on the item described as class = ', class, 'id = ', major_id  
    FROM sys.database_permissions AS DP  
    JOIN sys.database_principals AS DPUsers  
        ON DP.grantee_principal_id = DPUsers.principal_id;  
    ```  
  
## <a name="RestoreProc"></a>データベースのアクセス許可に関するベスト プラクティス  
  
-   現実的な最も細かいレベルのアクセス許可を付与します。 権限を付与する、テーブルまたはビュー レベルのアクセス許可を管理できなくなる可能性があります。 データベース レベルで権限を付与するも許容度が高い可能性があります。 データベースが作業の境界を定義するスキーマで設計されている場合はおそらくスキーマ権限の付与は、テーブル レベルおよびデータベース レベルの適切なバランスです。  
  
-   ユーザーまたはログインではなく、ロールにアクセス許可を付与します。 権限を管理するユーザーの代わりにロールを使用して簡単にすばやく付与またはロールの内外に移動することによって、ユーザーまたはログインの権限のセットを取り消します。 関数が別に 1 人のユーザーから成功したとき、権限はロール メンバーシップの変更中にロール レベルではそのままです。  
  
-   ジョブの関数とアクションを実行する会社のグループに基づくジョブ関数の役割を結合する上位レベルのグループのロールに基づいてロールへのアクセス許可を付与します。  
  
-   すべてのエンド ユーザー固有のログインが必要です。 ユーザーがログインの共有はできません。 各ユーザーのログインを提供することにより、監査証跡と、アクセス許可の管理を簡略化します。  
  
## <a name="fixed-database-roles"></a>固定データベース ロール
SQL Server では、サーバーに対する権限を管理するために事前構成済みの (固定) データベース レベル ロールを提供します。 割り当てられているアクセス許可を変更することはできませんが、事前構成済みのロールが固定されています。 ユーザー定義データベース ロールを作成することもできます。 ユーザー定義データベース ロールに割り当てられたアクセス許可を変更することができます。  
  
ロールは、その他のプリンシパルをグループ化するセキュリティ プリンシパルです。 データベース ロールは、データベース全体でその権限のスコープ。 データベース ユーザーおよびその他のデータベース ロールは、データベース ロールのメンバーとして追加できます。 固定データベース ロールは、相互に追加できません。 (*ロール* は、Windows オペレーティング システムの *グループ* に似ています)。  
  
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
  
### <a name="permissions-of-the-fixed-database-roles"></a>固定データベース ロールのアクセス許可  
固定サーバー ロールと固定データベース ロールのシステムは、1980 で生成されたレガシ システムです。 固定ロールは引き続きサポートし、は、いくつかのユーザーが存在し、セキュリティ ニーズは単純な環境で便利です。 SQL Server 2005 以降では、アクセス許可を付与の詳細なシステムが作成されました。 この新しいシステムより詳細な許可と権限の拒否の両方の多くのオプションを提供することです。 詳細なシステムの複雑さが増してなりますについては、困難になりますが、ほとんどのエンタープライズ システムは、固定ロールを使用する代わりにアクセス許可を付与する必要があります。 <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md). -->各固定データベース ロールに関連付けられているアクセス許可を次に示します。 この SQL Server のグラフィックにすべてのアクセス許可がないと、使用可能な (または必要に応じて) AP でします。  
  
![APS セキュリティの固定データベース ロール](./media/pdw-permissions/APS_security_fixed_db_roles.png "APS_security_fixed_db_roles")  
  
### <a name="related-content"></a>関連コンテンツ  
  
-   ユーザー定義ロールを作成するを参照してください。 [CREATE ROLE](../t-sql/statements/create-role-transact-sql.md)します。  
  
  
## <a name="fixed-server-roles"></a>固定サーバー ロール
固定サーバー ロールは、SQL Server によって自動的に作成されます。 SQL Server PDW では、SQL Server の固定サーバー ロールの制限の実装があります。 のみ、 **sysadmin**と**パブリック**メンバーとしてユーザーのログインを持ちます。 **Setupadmin**と**dbcreator**ロールは、SQL Server PDW で内部的に使用されます。 追加のメンバーを追加または任意のロールから削除できません。  
  
### <a name="sysadmin-fixed-server-role"></a>sysadmin 固定サーバー ロール  
**sysadmin** 固定サーバー ロールのメンバーは、サーバーに対するすべての操作を実行できます。 **Sa**ログインが唯一のメンバー、 **sysadmin**固定サーバー ロール。 追加のログインを追加できません、 **sysadmin**固定サーバー ロール。 **CONTROL SERVER** アクセス許可を付与すると、**sysadmin** 固定サーバー ロールのメンバーシップが概算されます。 次の例、 **CONTROL SERVER** Fay という名前のログインに許可します。  
  
```sql  
USE master;  
GO  
GRANT CONTROL SERVER TO Fay;  
```  
  
> [!IMPORTANT]  
> **CONTROL SERVER**アクセス許可が SQL Server PDW のほぼ完全に制御を提供します。 可能であれば、ログインをきめ細かなアクセス許可を提供します。 たとえば、許可、 **VIEW SERVER STATE**、 **ALTER ANY LOGIN**、 **VIEW ANY DATABASE**、または**CREATE ANY DATABASE**アクセス許可。  
  
### <a name="public-server-role"></a>public サーバー ロール  
ログインは、SQL Server PDW に接続できるすべてのメンバーである、**パブリック**サーバーの役割。 すべてのログインに許可する権限を継承する**パブリック**で任意のオブジェクト。 のみを割り当てる**パブリック**すべてのユーザーに使用できるオブジェクトの場合、オブジェクトに対するアクセス許可。 メンバーシップを変更することはできません、**パブリック**ロール。  
  
> [!NOTE]  
> **パブリック**他のロールとは異なる実装されます。 すべてのサーバー プリンシパルのメンバーシップ、public のメンバーであるため、**パブリック**ロールが表示されていない、 **sys.server_role_members** DMV。  
  
### <a name="fixed-server-roles-vs-granting-permissions"></a>固定サーバー ロールと権限を付与します。  
固定サーバー ロールと固定データベース ロールのシステムは、1980 で生成されたレガシ システムです。 固定ロールは引き続きサポートし、は、いくつかのユーザーが存在し、セキュリティ ニーズは単純な環境で便利です。 SQL Server 2005 以降では、アクセス許可を付与の詳細なシステムが作成されました。 この新しいシステムより詳細な許可と権限の拒否の両方の多くのオプションを提供することです。 詳細なシステムの複雑さが増してなりますについては、困難になりますが、ほとんどのエンタープライズ システムは、固定ロールを使用する代わりにアクセス許可を付与する必要があります。 <!-- MISSING LINKS The permissions are discussed and listed in the topic [Permissions: GRANT, DENY, REVOKE &#40;SQL Server PDW&#41;](../sqlpdw/permissions-grant-deny-revoke-sql-server-pdw.md).  -->  
  
## <a name="related-topics"></a>関連トピック  
  
- [権限の許可](grant-permissions.md)

<!-- MISSING LINKS
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->

