---
title: "許可を拒否する取り消す Perms-Azure SQL データと並列データ ウェアハウス |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5a3b7424-408e-4cb0-8957-667ebf4596fc
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c46d4df3d19b2c548b203f62a14ea4ebc0226296
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse"></a>アクセス許可: GRANT、DENY、REVOKE (Azure SQL Data Warehouse、並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  使用して[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] **GRANT**と**DENY**ステートメントを許可または拒否する権限 (など**更新**) でセキュリティ保護可能な (など、データベース、テーブル、ビュー、などです。)セキュリティ プリンシパル (ログイン、データベース ユーザー、またはデータベース ロール) です。 使用して**取り消す**許可を削除したり、権限の拒否します。  
  
 サーバー レベルのアクセス許可は、ログインに適用されます。 データベース レベルのアクセス許可は、データベースのユーザー ロールとデータベース ロールに適用されます。  
  
 どのようなアクセス許可を許可および拒否を表示するには、sys.server_permissions と sys.database_permissions ビューをクエリします。 権限を持つロールにメンバーシップがあるでは、明示的に許可またはセキュリティ プリンシパルに拒否されるアクセス許可を継承できます。 固定データベース ロールのアクセス許可は変更できなくなり、sys.server_permissions と sys.database_permissions ビューには表示されません。  
  
-   **GRANT** 1 つ以上のアクセス許可が明示的に許可します。  
  
-   **DENY**から 1 つまたは複数の権限を持つプリンシパルを明示的に拒否されます。  
  
-   **取り消す**既存削除**GRANT**または**DENY**アクセス許可。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>引数  
 \<アクセス許可 > [ **、**.*n* ]  
 1 つまたは複数のアクセス許可を付与するには、拒否、または取り消します。  
  
 ON [ \<class_type >::]*セキュリティ保護可能な*、 **ON**句は、セキュリティ保護可能なパラメーターをすると、付与、拒否、または revoke 権限の取り消しを説明します。  
  
 \<class_type > のセキュリティ保護可能なクラス型。 これは、**ログイン**、**データベース**、**オブジェクト**、**スキーマ**、**ロール**、または**ユーザー**. またに権限を付与できる、**サーバー * * * class_type*が**サーバー**これらのアクセス許可が指定されていません。 **データベース**、アクセス許可がという単語を含む場合が指定されていない**データベース**(たとえば**ALTER ANY DATABASE**)。 ない場合*class_type*が指定されているアクセス許可の種類は、サーバーまたはデータベース クラスに制限は、クラスを想定して**オブジェクト**です。  
  
 *securable*  
 ログイン、データベース、テーブル、ビュー、スキーマ、プロシージャ、ロール、またはを与えるには、ユーザーの名前は、拒否、または、アクセス許可を取り消します。 説明されている 3 部構成の名前付け規則では、オブジェクト名を指定できます[TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
 *プリンシパル*[ **、**.*n* ]  
 許可するには、1 つまたは複数のプリンシパルでは、拒否、または、アクセス許可を取り消します。 プリンシパルは、ログイン、データベース ユーザー、またはデータベース ロールの名前です。  
  
 FROM *principal* [ **,**...*n* ]  
 アクセス許可を取り消すの 1 つまたは複数のプリンシパル。  プリンシパルは、ログイン、データベース ユーザー、またはデータベース ロールの名前です。 **でのみ使用できます** 、 **取り消す** ステートメントです。 **で使用できる**  **GRANT** 、 **DENY** 、または **取り消す** です。  
  
 WITH GRANT OPTION  
 権限を許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 CASCADE  
 アクセス許可が拒否されるか、それが、指定したプリンシパルには、プリンシパルが権限を付与するその他のすべてのプリンシパルに失効したことを示します。 プリンシパルで権限のあるときに必要な**GRANT OPTION**です。  
  
 GRANT OPTION FOR  
 指定した権限を与える許可を取り消します。 これは、使用しているときに必要な**CASCADE**引数。  
  
> [!IMPORTANT]  
>  プリンシパルがなく、指定した権限を持っている場合、 **GRANT**オプション、権限自体が取り消されます。  
  
## <a name="permissions"></a>権限  
 アクセス許可を付与する権限の許可者が必要か、権限自体で、 **WITH GRANT OPTION**、上位の権限が与えられるアクセス許可のことを意味する必要がありますか。  オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 持つプリンシパル**コントロール**に対するセキュリティ保護可能な権限が権限を許可できますをセキュリティ保護可能な。  メンバー、 **db_owner**と**db_securityadmin**固定データベース ロールがデータベースにアクセス許可を付与できます。  
  
## <a name="general-remarks"></a>全般的な解説  
 拒否、またはプリンシパルに権限の取り消しは、承認が経過して、現在実行中の要求は影響しません。 アクセスを制限するには、すぐにする必要がありますのアクティブな要求を取り消すか現在のセッションを強制終了します。  
  
> [!NOTE]  
>  ほとんどの固定サーバー ロールは、このリリースでご利用いただけません。 ユーザー定義データベース ロールを使用してください。 ログインを追加することはできません、 **sysadmin**固定サーバー ロール。 許可、 **CONTROL SERVER**権限のメンバーシップを概算するため、 **sysadmin**固定サーバー ロール。  
  
 いくつかのステートメントでは、複数のアクセス許可が必要です。 たとえば、テーブルを作成する必要があります、 **CREATE TABLE** 、データベース内の権限および**ALTER SCHEMA**テーブルを格納するテーブルに対する権限。  
  
 PDW は、場合によって計算ノードとユーザーの操作を配布するストアド プロシージャを実行します。 そのため、データベース全体に対する execute 権限を拒否できません。 (たとえば`DENY EXECUTE ON DATABASE::<name> TO <user>;`は失敗します)。回避策としてには、ユーザー スキーマまたは特定のオブジェクト (プロシージャ) するには、execute 権限を拒否します。  
  
### <a name="implicit-and-explicit-permissions"></a>暗黙的および明示的なアクセス許可  
 *明示的なアクセス許可*は、 **GRANT**または**DENY**でプリンシパルに付与するアクセス許可、 **GRANT**または**DENY**ステートメントです。  
  
 *暗黙のアクセス許可*は、 **GRANT**または**DENY**プリンシパル (ログイン、ユーザー、またはデータベース ロール) は、別のデータベース ロールから継承したアクセス許可。  
  
 暗黙のアクセス許可は、包含または親のアクセス許可からも継承できます。 たとえば、**更新**用意することによって、テーブルに対する権限を継承できる**更新**テーブルを含むスキーマの権限または**コントロール**テーブルに対する権限。  
  
### <a name="ownership-chaining"></a>所有権の継承  
 複数のデータベース オブジェクトへのアクセス相互順番に、シーケンスと呼ばれます、*チェーン*です。 このようなチェーンは独立して存在しない、ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、チェーン内のリンクを通過[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトとは別にアクセスした場合よりも、異なる方法で構成要素であるオブジェクトに対する権限を評価します。 所有権の継承は、セキュリティを管理するための重要な影響を与えます。 所有権の継承の詳細については、次を参照してください。[所有権の継承](http://msdn.microsoft.com/en-us/library/ms188676\(v=sql11\).aspx)と[チュートリアル: 所有権の継承とコンテキストの切り替え](http://msdn.microsoft.com/en-us/library/bb153640\(v=sql11\).aspx)です。  
  
## <a name="permission-list"></a>アクセス許可の一覧  
  
### <a name="server-level-permissions"></a>サーバー レベルのアクセス許可  
 サーバー レベルの権限を許可、拒否されると、およびログインから取り消します。  
  
 **サーバーに適用される権限**  
  
-   CONTROL SERVER  
  
-   ADMINISTER BULK OPERATIONS  
  
-   ALTER ANY CONNECTION  
  
-   ALTER ANY DATABASE  
  
-   CREATE ANY DATABASE  
  
-   すべての外部データ ソースを変更します。  
  
-   任意の外部のファイル形式を変更します。  
  
-   ALTER ANY LOGIN  
  
-   ALTER SERVER STATE  
  
-   CONNECT SQL  
  
-   VIEW ANY DEFINITION  
  
-   VIEW ANY DATABASE  
  
-   VIEW SERVER STATE  
  
 **ログインに適用される権限**  
  
-   ログインの CONTROL 権限  
  
-   ログインの ALTER 権限します。  
  
-   ログインに権限を借用します。  
  
-   VIEW DEFINITION  
  
### <a name="database-level-permissions"></a>データベース レベルのアクセス許可  
 データベース レベルのアクセス許可の付与、拒否、および失効したデータベース ユーザーおよびユーザー定義のデータベース ロールからです。  
  
 **すべてのデータベース クラスに適用される権限**  
  
-   CONTROL  
  
-   ALTER  
  
-   VIEW DEFINITION  
  
 **ユーザー以外のすべてのデータベース クラスに適用される権限**  
  
-   TAKE OWNERSHIP  
  
 **データベースのみに適用されるアクセス許可**  
  
-   ALTER ANY DATABASE  
  
-   データベースの ALTER 権限します。  
  
-   ALTER ANY DATASPACE  
  
-   ALTER ANY ROLE  
  
-   ALTER ANY SCHEMA  
  
-   ALTER ANY USER  
  
-   BACKUP DATABASE  
  
-   データベース上の接続します。  
  
-   CREATE PROCEDURE  
  
-   CREATE ROLE  
  
-   CREATE SCHEMA  
  
-   CREATE TABLE  
  
-   CREATE VIEW  
  
-   SHOWPLAN  
  
 **ユーザーにのみ適用されるアクセス許可**  
  
-   IMPERSONATE  
  
 **データベース、スキーマ、およびオブジェクトに適用される権限**  
  
-   ALTER  
  
-   DELETE  
  
-   EXECUTE  
  
-   INSERT  
  
-   SELECT  
  
-   UPDATE  
  
-   REFRENCES  
  
 アクセス許可の種類の定義では、次を参照してください。[権限 (データベース エンジン)](http://msdn.microsoft.com/library/ms191291.aspx)です。  
  
### <a name="chart-of-permissions"></a>アクセス許可のグラフ  
 すべてのアクセス許可は、このポスターでグラフィカルに表されます。 これは、権限の階層構造を入れ子になったを確認する最も簡単な方法です。 たとえば、 **ALTER ON LOGIN**自体には、アクセス許可を与えることができますが、ログインが与えられている場合にも含まれる、**コントロール**そのログインに対する権限、ログインが与えられている場合、または、 **ALTER ANYログイン**権限です。  
  
 ![APS セキュリティの権限ポスター](../../t-sql/statements/media/aps-security-perms-poster.png "APS セキュリティの権限ポスター")  
  
 このポスターのフル サイズ バージョンをダウンロードするを参照してください。 [SQL Server PDW のアクセス許可](http://go.microsoft.com/fwlink/?LinkId=244249)AP Yammer サイトのファイルのセクションで (またはからの電子メールによる要求 **apsdoc@microsoft.com**です。  
  
## <a name="default-permissions"></a>既定の権限  
 次の一覧には、既定のアクセス許可について説明します。  
  
-   使用してログインを作成するときに、 **CREATE LOGIN**ステートメントは、新しいログインを受け取る、 **CONNECT SQL**権限です。  
  
-   すべてのログインのメンバーである、**パブリック**サーバーの役割から削除することはできません**パブリック**です。  
  
-   使用して、データベース ユーザーを作成するときに、 **CREATE USER**権限、データベース ユーザーの受信、**接続**データベースの権限です。  
  
-   含む、すべてのプリンシパル、**パブリック**ロール、既定では明示的または暗黙的な権限を持っていません。  
  
-   ログインまたはユーザーは、データベースまたはオブジェクトの所有者になると、ログインまたはユーザー常には、データベースまたはオブジェクトに対してすべてのアクセスを許可します。 所有者のアクセス許可では、変更することはできませんし、明示的なアクセス許可として表示されません。 **GRANT**、 **DENY**、および**取り消す**ステートメントが所有者に影響を与えるありません。  
  
-   **Sa**ログインがアプライアンス上のすべてのアクセス許可を持っています。 所有者のアクセス許可のような**sa**アクセス許可が変更することはできず、、明示的なアクセス許可として表示されません。 **GRANT**、 **DENY**、および**取り消す**ステートメントがあるない影響**sa**ログインします。 **Sa**ログインの名前を変更することはできません。  
  
-   **使用**ステートメントでは、権限は必要ありません。 すべてのプリンシパルが実行できる、**使用**任意のデータベース上のステートメント。  
  
##  <a name="Examples"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-granting-a-server-level-permission-to-a-login"></a>A. ログインにサーバー レベル権限を許可します。  
 次の 2 つのステートメントでは、ログインに、サーバー レベルの権限を付与します。  
  
```  
GRANT CONTROL SERVER TO [Ted];  
```  
  
```  
GRANT ALTER ANY DATABASE TO Mary;  
```  
  
### <a name="b-granting-a-server-level-permission-to-a-login"></a>B. ログインにサーバー レベル権限を許可します。  
 次の例では、サーバー プリンシパル (別のログイン) へのログインに、サーバー レベルの権限を付与します。  
  
```  
GRANT  VIEW DEFINITION ON LOGIN::Ted TO Mary;  
```  
  
### <a name="c-granting-a-database-level-permission-to-a-user"></a>C. データベース レベル権限をユーザーに許可します。  
 次の例では、データベース プリンシパル (別のユーザー) にユーザーのデータベース レベルのアクセス許可を付与します。  
  
```  
GRANT VIEW DEFINITION ON USER::[Ted] TO Mary;  
```  
  
### <a name="d-granting-denying-and-revoking-a-schema-permission"></a>D. 許可、拒否、およびスキーマの権限を取り消す  
 次**GRANT**ステートメントが任意のテーブルまたは dbo スキーマにビューからデータを選択する権限を Yuen に付与します。  
  
```  
GRANT SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 次**DENY**ステートメントでは、任意のテーブルまたは dbo スキーマにビューからデータの選択を Yuen ができないようにします。 Yuen 場合でも、ロールのメンバーシップを通じてなどその他の何らかの方法での権限を持って彼は、データを読み取ることはできません。  
  
```  
DENY SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 次**取り消す**ステートメントを削除、 **DENY**権限です。 今すぐ Yuen の明示的なアクセス許可は、ニュートラルです。 Yuen では、ロールのメンバーシップなどその他のいくつかの暗黙的な権限を任意のテーブルからデータを選択できる場合があります。  
  
```  
REVOKE SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
### <a name="e-demonstrating-the-optional-object-clause"></a>E. 省略可能なオブジェクトを示す:: 句  
 オブジェクトは、権限ステートメントの既定のクラスであるために、次の 2 つのステートメントは同じです。 **オブジェクト::**句は省略可能です。  
  
```  
GRANT UPDATE ON OBJECT::dbo.StatusTable TO [Ted];  
```  
  
```  
GRANT UPDATE ON dbo.StatusTable TO [Ted];  
```  
  
  

