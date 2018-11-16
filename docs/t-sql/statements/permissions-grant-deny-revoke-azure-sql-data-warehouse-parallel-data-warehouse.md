---
title: GRANT-DENY-REVOKE Perms-Azure SQL データおよび並列データ ウェアハウス | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5a3b7424-408e-4cb0-8957-667ebf4596fc
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ee7b41d2c6e4584bd2dd48dec09fbe71b5150d13
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696780"
---
# <a name="permissions-grant-deny-revoke-azure-sql-data-warehouse-parallel-data-warehouse"></a>アクセス許可: GRANT、DENY、REVOKE (Azure SQL Data Warehouse、並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  セキュリティ保護可能なリソース (データベース、テーブル、ビューなど) からセキュリティ プリンシパル (ログイン、データベース ユーザー、またはデータベース ロール) にアクセス許可 (**UPDATE** など) を付与または拒否するには、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] または [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]**GRANT** および **DENY** ステートメントを使用します。 アクセス許可を許可または拒否するには、**REVOKE** を使用します。  
  
 サーバー レベルのアクセス許可は、ログインに適用されます。 データベース レベルのアクセス許可は、データベースのユーザー ロールとデータベース ロールに適用されます。  
  
 どのようなアクセス許可が許可および拒否されているかを表示するには、sys.server_permissions および sys.database_permissions ビューのクエリを実行します。 権限を持つロールにメンバーシップがあるでは、明示的に許可またはセキュリティ プリンシパルに拒否されるアクセス許可を継承できます。 固定データベース ロールのアクセス許可は変更できず、sys.server_permissions および sys.database_permissions ビューは表示されません。  
  
-   **GRANT** は、明示的に 1 つまたは複数のアクセス許可を付与します。  
  
-   **DENY** は、1 つまたは複数の権限を持つプリンシパルを明示的に拒否します。  
  
-   **REVOKE** は、既存の **GRANT** または **DENY** アクセス許可を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 \<permission>[ **,**...*n* ]  
 1 つまたは複数のアクセス許可を付与するには、拒否、または取り消します。  
  
 ON [ \<class_type> :: ] *securable* **ON** 句は、アクセス許可を許可、拒否、または削除するセキュリティ保護可能なパラメーターを記述します。  
  
 \<class_type> セキュリティ保護可能なクラス型。 これは、**LOGIN**、**DATABASE**、**OBJECT**、**SCHEMA**、**ROLE**、または **USER** です。 **SERVER**_class\_type_ にアクエス許可を付与することもできますが、**SERVER** は、これらのアクセス許可に対して指定されません。 **DATABASE** は、アクセス許可に **DATABASE** という単語が含まれる場合 (たとえば **ALTER ANY DATABASE**) 指定されません。 *class_type* が指定されておらず、アクセス許可のタイプがサーバーまたはデータベースのクラスに制限されていない場合、クラスは **OBJECT** と見なされます。  
  
 *securable*  
 ログイン、データベース、テーブル、ビュー、スキーマ、プロシージャ、ロール、またはを与えるには、ユーザーの名前は、拒否、または、アクセス許可を取り消します。 「[Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)」で説明されている 3 部構成の名前付け規則を使用してオブジェクトの名前を指定することができます。  
  
 TO *principal* [ **,**...*n* ]  
 許可するには、1 つまたは複数のプリンシパルでは、拒否、または、アクセス許可を取り消します。 プリンシパルは、ログイン、データベース ユーザー、またはデータベース ロールの名前です。  
  
 FROM *principal* [ **,**...*n* ]  
 アクセス許可を取り消すの 1 つまたは複数のプリンシパル。  プリンシパルは、ログイン、データベース ユーザー、またはデータベース ロールの名前です。 **FROM** は、**REVOKE** ステートメントでのみ使用できます。 **TO** は、**GRANT**、**DENY**、または **REVOKE** で使用できます。  
  
 WITH GRANT OPTION  
 権限を許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 CASCADE  
 アクセス許可が拒否されるか、それが、指定したプリンシパルには、プリンシパルが権限を付与するその他のすべてのプリンシパルに失効したことを示します。 このオプションは、**GRANT OPTION** を使用してプリンシパルに権限が与えられている場合に必要となります。  
  
 GRANT OPTION FOR  
 指定した権限を与える許可を取り消します。 **CASCADE** 引数を使用する場合、この引数は必須です。  
  
> [!IMPORTANT]  
>  権限が **GRANT** オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
## <a name="permissions"></a>アクセス許可  
 アクセス許可を付与するには、権限の許可者が、**WITH GRANT OPTION** でアクセス許可自体を持っているか、アクセス許可が付与されたことを意味する上位の権限を持っている必要があります。  オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 セキュリティ保護可能なリソースに対して **CONTROL** 権限があるプリンシパルは、そのリソースの権限を許可できます。  **db_owner** および **db_securityadmin** 固定データベース ロールのメンバーは、データベース内のすべてのアクセス権を付与できます。  
  
## <a name="general-remarks"></a>全般的な解説  
 拒否、またはプリンシパルに権限の取り消しは、承認が経過して、現在実行中の要求は影響しません。 アクセスを制限するには、すぐにする必要がありますのアクティブな要求を取り消すか現在のセッションを強制終了します。  
  
> [!NOTE]  
>  ほとんどの固定サーバー ロールは、このリリースでご利用いただけません。 ユーザー定義データベース ロールを使用してください。 **sysadmin** 固定サーバー ロールにログインを追加することはできません。 **CONTROL SERVER** アクセス許可を付与すると、**sysadmin** 固定サーバー ロールのメンバーシップが概算されます。  
  
 いくつかのステートメントでは、複数のアクセス許可が必要です。 たとえば、テーブルを作成するには、データベースの **CREATE TABLE** アクセス許可が必要であり、テーブルが含まれるテーブルの場合は **ALTER SCHEMA** アクセス許可が必要です。  
  
 PDW は、場合によって計算ノードとユーザーの操作を配布するストアド プロシージャを実行します。 そのため、データベース全体に対する execute 権限を拒否できません。 (たとえば `DENY EXECUTE ON DATABASE::<name> TO <user>;` は失敗します)。回避策としてには、ユーザー スキーマまたは特定のオブジェクト (プロシージャ) するには、execute 権限を拒否します。  
  
### <a name="implicit-and-explicit-permissions"></a>暗黙的および明示的なアクセス許可  
 *明示的なアクセス許可*は、**GRANT** または **DENY** ステートメントによってプリンシパルに付与される **GRANT** または **DENY** アクセス許可です。  
  
 *暗黙的なアクセス許可*は、プリンシパル (ログイン、ユーザー、データベース ロール) が別のデータベース ロールから継承する **GRANT** または **DENY** アクセス許可です。  
  
 暗黙のアクセス許可は、包含または親のアクセス許可からも継承できます。 たとえば、テーブルの **UPDATE** アクセス許可は、テーブルが含まれるスキーマに対する **UPDATE** アクセス許可、またはテーブルの **CONTROL** アクセス許可を持つことによって継承できます。  
  
### <a name="ownership-chaining"></a>組み合わせ所有権  
 複数のデータベース オブジェクトが連続して互いにアクセスしている場合、このシーケンスは*チェーン*と呼ばれます。 このようなチェーンは単独では存在しませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がチェーン内のリンクを移動する際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、構成要素であるオブジェクトに対する権限が、オブジェクトに個別にアクセスした場合とは異なる方法で評価されます。 所有権の継承は、セキュリティを管理するための重要な影響を与えます。 所有権の継承の詳細については、次を参照してください「[所有権の継承](https://msdn.microsoft.com/library/ms188676\(v=sql11\).aspx)」および「[チュートリアル: 所有権の継承とコンテキストの切り替え](../../relational-databases/tutorial-ownership-chains-and-context-switching.md)」です。  
  
## <a name="permission-list"></a>アクセス許可の一覧  
  
### <a name="server-level-permissions"></a>サーバー レベルのアクセス許可  
 サーバー レベルの権限を許可、拒否されると、およびログインから取り消します。  
  
 **サーバーに適用されるアクセス許可**  
  
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
  
 **データベースのすべてのクラスに適用される権限**  
  
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
  
-   Del  
  
-   EXECUTE  
  
-   INSERT  
  
-   SELECT  
  
-   UPDATE  
  
-   REFRENCES  
  
 各権限の種類の定義については、「[権限 (データベース エンジン)](https://msdn.microsoft.com/library/ms191291.aspx)」を参照してください。  
  
### <a name="chart-of-permissions"></a>アクセス許可のグラフ  
 すべてのアクセス許可は、このポスターでグラフィカルに表されます。 これは、権限の階層構造を入れ子になったを確認する最も簡単な方法です。 たとえば、**ALTER ON LOGIN** 自体でアクセス許可を与えることができますが、ログインがそのログインに対する **CONTROL** アクセス許可を与えられている場合、またはログインが **ALTER ANY LOGIN** アクセス許可を与えられている場合にも含まれます。  
  
 ![APS セキュリティの権限ポスター](../../t-sql/statements/media/aps-security-perms-poster.png "APS セキュリティの権限ポスター")  
  
 このポスターのフル サイズ バージョンをダウンロードするには、APS Yammer サイトのファイルのセクションの「[SQL Server PDW のアクセス許可](https://go.microsoft.com/fwlink/?LinkId=244249)」を参照してください (または **apsdoc@microsoft.com** に電子メールで要求してください)。  
  
## <a name="default-permissions"></a>既定の権限  
 次の一覧には、既定のアクセス許可について説明します。  
  
-   **CREATE LOGIN** ステートメントを使用してログインを作成するときに、新しいログインは **CONNECT SQL** アクセス トークンを付与されます。  
  
-   すべてのログインは、**public** サーバー ロールのメンバーであり、**public** から削除することはできません。  
  
-   **CREATE USER** アクセス許可を使用してデータベースユーザーを作成するときには、データベース ユーザーがデータベース内の **CONNECT** アクセス許可を付与されます。  
  
-   **パブリック** ロールを含むすべてのプリンシパルは、既定では明示的または暗黙的なアクセス許可を持っていません。  
  
-   ログインまたはユーザーは、データベースまたはオブジェクトの所有者になると、ログインまたはユーザー常には、データベースまたはオブジェクトに対してすべてのアクセスを許可します。 所有者のアクセス許可では、変更することはできませんし、明示的なアクセス許可として表示されません。 **GRANT**、**DENY**、および **REVOKE** ステートメントは所有者に影響しません。  
  
-   **Sa** ログインは、アプライアンス上のすべてのアクセス許可を持っています。 所有者のアクセス許可と同様に、**sa** アクセス許可を変更することはできず、明示的なアクセス許可として表示されません。 **GRANT**、**DENY**、および **REVOKE** ステートメントは **sa** ログインに影響しません。 **Sa** ログインの名前を変更することはできません。  
  
-   **USE** ステートメントでは、権限は必要ありません。 すべてのプリンシパルが、**USE** ステートメントを任意のデータベース上で実行できます。  
  
##  <a name="Examples"></a> 例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
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
 次の **GRANT** ステートメントは、dbo スキーマの任意のテーブルまたはビューからデータを選択する権限を Yuen に付与します。  
  
```  
GRANT SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 次の **DENY** ステートメントでは、Yuen が dbo スキーマのどのテーブルまたはビューからもデータを選択できないようにします。 Yuen 場合でも、ロールのメンバーシップを通じてなどその他の何らかの方法での権限を持って彼は、データを読み取ることはできません。  
  
```  
DENY SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
 次の **REVOKE** ステートメントは **DENY** 権利を削除します。 今すぐ Yuen の明示的なアクセス許可は、ニュートラルです。 Yuen では、ロールのメンバーシップなどその他のいくつかの暗黙的な権限を任意のテーブルからデータを選択できる場合があります。  
  
```  
REVOKE SELECT ON SCHEMA::dbo TO [Yuen];  
```  
  
### <a name="e-demonstrating-the-optional-object-clause"></a>E. 省略可能なオブジェクトを示す:: 句  
 オブジェクトは、権限ステートメントの既定のクラスであるために、次の 2 つのステートメントは同じです。 **OBJECT::** 句は省略可能です。  
  
```  
GRANT UPDATE ON OBJECT::dbo.StatusTable TO [Ted];  
```  
  
```  
GRANT UPDATE ON dbo.StatusTable TO [Ted];  
```  
  
  

