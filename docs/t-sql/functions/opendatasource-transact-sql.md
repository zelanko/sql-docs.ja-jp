---
title: "OPENDATASOURCE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENDATASOURCE
- OPENDATASOURCE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENDATASOURCE function
- remote data access [SQL Server], OPENDATASOURCE
- ad hoc distributed queries
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: 5510b846-9cde-4687-8798-be9a273aad31
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e2ddb99a84c910c89aedaa086eb10e3f9de7abb9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="opendatasource-transact-sql"></a>OPENDATASOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リンク サーバー名を使用せずに、4 つの要素で構成されるオブジェクト名の一部としてアドホック接続情報を提供します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENDATASOURCE ( provider_name, init_string )  
```  
  
## <a name="arguments"></a>引数  
 *provider_name*  
 データ ソースにアクセスするときに使用される、OLE DB プロバイダーの PROGID として登録されている名前を指定します。 *provider_name*は、 **char**データ型、既定値はありません。  
  
 *init_string*  
 接続文字列は、同期先プロバイダーの IDataInitialize インターフェイスに渡されます。 プロバイダー文字列の構文はキーワードと値のペアなどのセミコロンで区切られたに基づいて: **'***keyword1*=*値***;***keyword2*=*値***'**です。  
  
 プロバイダーでサポートされる、特定のキーワードと値の組み合わせについては、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access SDK を参照してください。 このドキュメントには、基本構文が定義されています。 次の表に、最も頻繁に使用されるリストに含まれるキーワード、 *init_string*引数。  
  
|Keyword|OLE DB プロパティ|有効な値と説明|  
|-------------|---------------------|----------------------------------|  
|[データ ソース]|DBPROP_INIT_DATASOURCE|接続先のデータ ソースの名前。 この値の解釈は、プロバイダーによって異なります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー サーバーの名前を示します。 Jet OLE DB プロバイダーの場合、この値は .mdb ファイルまたは .xls ファイルのフル パスを表します。|  
|場所|DBPROP_INIT_LOCATION|接続先のデータベースの位置。|  
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|プロバイダー固有の接続文字列。|  
|Connect timeout|DBPROP_INIT_TIMEOUT|接続試行が失敗する基準となるタイムアウト値。|  
|[ユーザー ID]|DBPROP_AUTH_USERID|接続に使用されるユーザー ID。|  
|Password|DBPROP_AUTH_PASSWORD|接続に使用されるパスワード。|  
|Catalog|DBPROP_INIT_CATALOG|データ ソースに接続するときの初期カタログまたは既定のカタログの名前。|  
|Integrated Security|DBPROP_AUTH_INTEGRATED|Windows 認証を指定する SSPI。|  
  
## <a name="remarks"></a>解説  
 OPENDATASOURCE は、OLE DB データ ソースからリモート データにアクセスするときに使用できます。ただしこの場合、指定したプロバイダーに対して DisallowAdhocAccess レジストリ オプションが明示的に 0 に設定されており、Ad Hoc Distributed Queries 詳細構成オプションが有効になっている必要があります。 これらのオプションが設定されていない場合は、既定でアドホック接続は許可されません。  
  
 OPENDATASOURCE 関数は同じで使用できます[!INCLUDE[tsql](../../includes/tsql-md.md)]構文のリンク サーバー名としての場所。 つまり、この関数は、4 つの要素で構成される名前の先頭で、SELECT、INSERT、UPDATE、および DELETE ステートメント内のテーブル名やビュー名、または EXECUTE ステートメント内のリモート ストアド プロシージャを参照する要素として使用できます。 リモート ストアド プロシージャを実行する場合、OPENDATASOURCE では別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを参照する必要があります。 OPENDATASOURCE の引数に変数は指定できません。  
  
 OPENROWSET 関数と同様に、OPENDATASOURCE では、あまり頻繁にアクセスされない OLE DB データ ソースだけを参照してください。 頻繁にアクセスされるデータ ソースに対してはリンク サーバーを定義します。 OPENDATASOURCE でも OPENROWSET でも、リンク サーバー定義のすべての機能は提供されず、たとえばセキュリティ管理やカタログ情報に対してクエリを実行することはできません。 すべての接続情報は、パスワードを含め、OPENDATASOURCE を呼び出すたびに指定する必要があります。  
  
> [!IMPORTANT]  
>  Windows 認証はよりもはるかに安全な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 できるだけ Windows 認証を使用してください。 接続文字列では、OPENDATASOURCE と共に明示的なパスワードを指定しないでください。  
  
 各プロバイダーの接続要件は、リンク サーバー作成時におけるこれらのパラメーターの要件に似ています。 多くの一般的なプロバイダーの詳細については、トピックに記載されて[sp_addlinkedserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 FROM 句での OPENDATASOURCE、OPENQUERY、または OPENROWSET の呼び出しは、更新の対象として使用されるこれらの関数の呼び出しとは別に評価されます。これは、両方の呼び出しに同じ引数が指定されている場合にも当てはまります。 特に、いずれか一方の呼び出しの結果に適用されるフィルター条件または結合条件は、もう一方の結果に影響しません。  
  
## <a name="permissions"></a>Permissions  
 すべてのユーザーが OPENDATASOURCE を実行できます。 リモート サーバーへの接続に使用される権限は、接続文字列によって決まります。  
  
## <a name="examples"></a>使用例  
 次の例へのアドホック接続を作成、`Payroll`のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーで`London`、クエリ、および、`AdventureWorks2012.HumanResources.Employee`テーブル。 (SQLNCLI を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにリダイレクトされます)。  
  
```  
SELECT *  
FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source=London\Payroll;Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Employee  
```  
  
 次の例では、1997 - 2003 形式の Excel スプレッドシートへのアドホック接続を作成します。  
  
```  
SELECT * FROM OPENDATASOURCE('Microsoft.Jet.OLEDB.4.0',  
'Data Source=C:\DataFolder\Documents\TestExcel.xls;Extended Properties=EXCEL 5.0')...[Sheet1$] ;  
```  
  
## <a name="see-also"></a>参照  
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  
