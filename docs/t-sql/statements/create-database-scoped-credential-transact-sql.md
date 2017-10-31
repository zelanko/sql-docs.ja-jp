---
title: "データベース スコープの資格情報 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE SCOPED CREDENTIAL
- DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_TSQL
- CREATE_DATABASE_SCOPED_CREDENTIAL
- CREATE_DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL
helpviewer_keywords:
- DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], DATABASE SCOPED CREDENTIAL statement
ms.assetid: fe830577-11ca-44e5-953b-2d589d54d045
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 49ff2aa300fc8f8e74424ae6e334bee823e8176c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="create-database-scoped-credential-transact-sql"></a>データベース スコープ ベースの資格情報 (TRANSACT-SQL) の作成します。
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  データベースの資格情報を作成します。 データベースの資格情報は、サーバー ログインまたはデータベース ユーザーにマップされていません。 データベースは、資格情報を使用して、外部の場所へのアクセスをいつでも、データベースでは、アクセスが必要な操作を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
 
CREATE DATABASE SCOPED CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 作成するデータベース スコープの資格情報の名前を指定します。 *credential_name*シャープ (#) 記号で始めることはできません。 ## で始まる資格情報はシステム資格情報です。  
  
 IDENTITY **='***identity_name***'**  
 サーバーの外部に接続するときに使用するアカウントの名前を指定します。 Azure Blob ストレージからファイルをインポートするユーザー名がある必要があります`SHARED ACCESS SIGNATURE`です。  共有アクセス署名の詳細については、次を参照してください。[を使用して共有アクセス署名 (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)です。  
  
 シークレット**='***シークレット***'**  
 送信の認証に必要なシークレットを指定します。 `SECRET`Azure Blob ストレージからファイルをインポートするが必要です。   
>  [!WARNING]
>  SAS キーの値が始まる可能性があります、'?'(疑問符)。 SAS キーを使用する場合は、先頭を削除する必要があります '?' です。 それ以外の場合、作業がブロックされる可能性があります。  
  
## <a name="remarks"></a>解説  
 データベース スコープ資格情報は、外部のリソースに接続するために必要な認証情報を含むレコード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 通常、資格情報には Windows ユーザーとパスワードが含まれます。  
  
 スコープの資格情報をデータベースを作成する前に、データベースに、マスター _ キー資格情報を保護する必要があります。 詳細については、[CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)を参照してください。  
  
 IDENTITY が Windows ユーザーの場合、このシークレットにはパスワードを指定できます。 シークレットはサービス マスター キーを使用して暗号化されます。 サービス マスター キーが再生成された場合、シークレットは新しいサービス マスター キーを使用して再度暗号化されます。  
   
 データベース スコープ資格情報に関する情報は、 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)カタログ ビューです。  
  
 
 ここから一部のアプリケーション データベースの資格情報のスコープします。  
  
- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]非パブリックの Azure blob ストレージまたは PolyBase による Kerberos でセキュリティ保護された Hadoop クラスターにアクセスするのにには、データベース スコープ資格情報を使用します。 詳細については、次を参照してください。[外部データ ソースの作成 (TRANSACT-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)です。  

- [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]PolyBase で非パブリックの Azure blob ストレージにアクセスするデータベース スコープ資格情報を使用します。 詳細については、次を参照してください。[外部データ ソースの作成 (TRANSACT-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)です。
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベースのグローバル クエリ機能のスコープを持つ資格情報。 これは、複数のデータベース シャード間でクエリする機能です。  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベース スコープ資格情報を使用して Azure blob ストレージに拡張イベント ファイルを書き込みます。  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベースの柔軟なプールのスコープを持つ資格情報。 詳細については、次を参照してください[柔軟なデータベースの爆発的な増加を緩和する機能。](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)  

- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)と[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)を使用してデータベース スコープの資格情報を Azure blob ストレージからデータにアクセスします。 詳細については、次を参照してください。[例の一括データにアクセスする Azure Blob ストレージに](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)です。 
  
## <a name="permissions"></a>Permissions  
 必要があります**コントロール**データベースに対する権限。  
  
## <a name="examples"></a>使用例  
### <a name="a-creating-a-database-scoped-credential-for-your-application"></a>A. データベースを作成するには、アプリケーションの資格情報がスコープ設定されます。
 次の例と呼ばれるデータベース スコープ資格情報を作成する`AppCred`です。 データベース スコープ資格情報には、Windows ユーザーが含まれている`Mary5`とパスワード。  
  
```tsql  
-- Create a db master key if one does not already exist, using your own password.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';  
  
-- Create a database scoped credential.  
CREATE DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-database-scoped-credential-for-a-shared-access-signature"></a>B. データベースを作成するには、共有アクセス署名の資格情報がスコープ設定されます。   
次の例を作成するために使用するデータベース スコープ資格情報の作成、[外部データ ソース](../../t-sql/statements/create-external-data-source-transact-sql.md)を実行できるなどの一括操作について、 [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)と[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). 共有アクセス署名は、SQL Server、AP、または SQL DW に PolyBase では使用できません。
```tsql
CREATE DATABASE SCOPED CREDENTIAL MyCredentials  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```
  
### <a name="c-creating-a-database-scoped-credential-for-polybase-connectivity-to-azure-data-lake-store"></a>C. データベースを作成するには、Azure Data Lake Store への接続を PolyBase の資格情報がスコープ設定されます。  
次の例を作成するために使用するデータベース スコープ資格情報の作成、[外部データ ソース](../../t-sql/statements/create-external-data-source-transact-sql.md)、Azure SQL Data Warehouse に PolyBase が使用できます。

Azure Data Lake Store は、Azure Active Directory アプリケーションをサービスにサービスの認証を使用します。
ください[AAD アプリケーションを作成](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory)し、データベース スコープ資格情報を作成しようとする前に、client_id、OAuth_2.0_Token_EndPoint、およびキーを文書化します。

```tsql
CREATE DATABASE SCOPED CREDENTIAL ADL_User
WITH
    IDENTITY = '<client_id>@\<OAuth_2.0_Token_EndPoint>'
    SECRET = '<key>'
;
```  
  
  
  
## <a name="more-information"></a>詳細情報  
 [資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER データベース スコープの資格情報 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [データベース スコープの資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

