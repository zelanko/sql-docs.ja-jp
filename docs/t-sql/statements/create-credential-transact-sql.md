---
title: "資格情報 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREDENTIAL_TSQL
- SQL13.SWB.CREDENTIAL.GENERAL.F1
- CREATE CREDENTIAL
- CREATE_CREDENTIAL_TSQL
- CREDENTIAL
dev_langs: TSQL
helpviewer_keywords:
- SECRET clause
- authentication [SQL Server], credentials
- CREATE CREDENTIAL statement
- credentials [SQL Server], CREATE CREDENTIAL statement
ms.assetid: d5e9ae69-41d9-4e46-b13d-404b88a32d9d
caps.latest.revision: "51"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f0e46404d775da09f4aaeb7b9640dd2a35d3cfa2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー レベルの資格情報を作成します。 資格情報は、SQL Server の外部リソースへの接続に必要な認証情報を含むレコードです。 通常、資格情報には Windows ユーザーとパスワードが含まれます。 たとえば、いくつかの場所へのデータベースのバックアップの保存には、その場所にアクセスする特別な資格情報を提供する SQL Server が必要です。 詳細については、次を参照してください。[資格情報 (データベース エンジン)](../../relational-databases/security/authentication-access/credentials-database-engine.md)です。
  
> [!NOTE]  
>  資格情報をデータベース レベルの使用時に[CREATE DATABASE SCOPED CREDENTIAL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). 複数のデータベース サーバーで、同じ資格情報を使用する必要がある場合は、サーバー レベルの資格情報を使用します。 データベースの移植性を高めるようにするのにには、データベース スコープの資格情報を使用します。 新しいサーバーにデータベースを移動すると、データベース スコープ資格情報がそれに移動します。 使用するデータベース スコープの資格情報[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 作成する資格情報の名前を指定します。 *credential_name*シャープ (#) 記号で始めることはできません。 ## で始まる資格情報はシステム資格情報です。  共有アクセス署名 (SAS) を使用する場合、この名前は、コンテナーのパスを一致する必要があります https で起動し、スラッシュを含めることはできません。 D は次の例を参照してください。  
  
 IDENTITY **='***identity_name***'**  
 サーバーの外部に接続するときに使用するアカウントの名前を指定します。 資格情報を使用して、Azure Key Vault にアクセスする場合、 **IDENTITY** key vault の名前を指定します。 後半の例 C を参照してください。 共有アクセス署名 (SAS) を使用しているとき、資格情報、 **IDENTITY**は*SHARED ACCESS SIGNATURE*です。 D は次の例を参照してください。  
  
 シークレット**='***シークレット***'**  
 送信の認証に必要なシークレットを指定します。  
  
 Azure Key Vault にアクセスする資格情報を使用する場合、**シークレット**の引数**CREATE CREDENTIAL**が必要です、 *\<クライアント ID >* (ハイフンなし)および*\<シークレット >*の**サービス プリンシパル**スペースを含めずに間でまとめて渡される Azure Active Directory でします。 後半の例 C を参照してください。 共有アクセス署名を使用しているとき、資格情報、**シークレット**共有アクセス署名トークンです。 D は次の例を参照してください。  Azure のコンテナーに保存されているアクセス ポリシーと shared access signature を作成する方法の詳細については、次を参照してください。[レッスン 1: Azure のコンテナーに保存されているアクセス ポリシーと shared access signature を作成する](../../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)です。  
  
 暗号化サービス プロバイダーの*cryptographic_provider_name*  
 名前を指定、*企業キー管理プロバイダー (EKM)*です。 キー管理の詳細については、次を参照してください。[拡張キー管理 &#40;です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>解説  

 IDENTITY が Windows ユーザーの場合、このシークレットにはパスワードを指定できます。 シークレットはサービス マスター キーを使用して暗号化されます。 サービス マスター キーが再生成された場合、シークレットは新しいサービス マスター キーを使用して再度暗号化されます。  
  
 資格情報を作成した後にマップできます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用してログイン[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)または[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)です。 A[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインは 1 つだけの資格情報にマップすることができますが、1 つの資格情報を複数にマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 詳細については、次を参照してください。[資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)です。 サーバー レベルの資格情報は、データベース ユーザーが、ログインにのみマップできます。 
  
 資格情報に関する情報は、 [sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)カタログ ビューです。  
  
 ログインにマップされたプロバイダーの資格情報がない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントにマップされた資格情報が使用されます。  
  
 それぞれが異なるプロバイダーで使用される資格情報であれば、1 つのログインに複数の資格情報をマップできます。 マップされた資格情報は、各ログインで各プロバイダーにつき 1 つだけ存在する必要があります。 同じ資格情報を他のログインにマップすることはできます。  
  
## <a name="permissions"></a>Permissions  
 必要があります**ALTER ANY CREDENTIAL**権限です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-basic-example"></a>A. 基本の例  
 次の例では、資格情報 `AlterEgo` を作成します。 資格情報には、Windows ユーザーが含まれている`Mary5`とパスワード。  
  
```  
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-credential-for-ekm"></a>B. EKM の資格情報の作成  
 次の例と呼ばれる以前に作成したアカウントを使用して`User1OnEKM`EKM 管理ツールでは、基本的な勘定科目の種類とパスワードを EKM モジュールにします。 **Sysadmin**サーバー上のアカウントを代入して、EKM アカウントへの接続に使用する資格情報を作成、 `User1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アカウント。  
  
```  
CREATE CREDENTIAL CredentialForEKM  
    WITH IDENTITY='User1OnEKM', SECRET='<EnterStrongPasswordHere>'  
    FOR CRYPTOGRAPHIC PROVIDER MyEKMProvider;  
GO  
  
/* Modify the login to assign the cryptographic provider credential */  
ALTER LOGIN Login1  
ADD CREDENTIAL CredentialForEKM;  
  
/* Modify the login to assign a non cryptographic provider credential */   
ALTER LOGIN Login1  
WITH CREDENTIAL = AlterEgo;  
GO  
```  
  
### <a name="c-creating-a-credential-for-ekm-using-the-azure-key-vault"></a>C. Azure のキー コンテナーを使用して EKM の資格情報の作成  
 次の例を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の資格情報、[!INCLUDE[ssDE](../../includes/ssde-md.md)]を使用して、Azure Key Vault にアクセスするときに使用する、 **SQL Server コネクタ for Microsoft Azure Key Vault**です。 使用しての完全な例については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コネクタを参照してください[拡張を使用して Azure Key Vault キー管理 &#40;SQL Server &#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
> [!IMPORTANT]  
>  **CREATE CREDENTIAL** の **IDENTITY** 引数には、資格情報コンテナー名が必要です。 **シークレット**の引数**CREATE CREDENTIAL**が必要です、 *\<クライアント ID >* (ハイフンなし) と*\<シークレット >*スペースを含めずに間でまとめて渡されます。  
  
 次の例で、 **クライアント ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) はハイフンを削除した文字列 `EF5C8E094D2A4A769998D93440D8115D` として入力し、 **シークレット** は文字列 *SECRET_DBEngine*として入力しています。  
  
```  
USE master;  
CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault',   
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
```  
  
 次の例の変数を使用して、同じ資格情報を作成する、**クライアント ID**と**シークレット**が連結して 1 つのフォームに、文字列、**シークレット**引数。 **置換**関数を使用して、クライアントの ID からハイフンを削除  
  
```  
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';  
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';  
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;  
  
EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');  
```  
  
### <a name="d-creating-a-credential-using-a-sas-token"></a>D. SAS トークンを使用して資格情報の作成  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)します。  
  
 次の例では、SAS トークンを使用して共有アクセス署名資格情報を作成します。  チュートリアルについては、Azure のコンテナーに保存されているアクセス ポリシーと shared access signature を作成すると、共有アクセス署名を使用して資格情報を作成し、次を参照してください[チュートリアル: SQL Server 2016 で、Microsoft Azure Blob ストレージ サービスの使用。データベース](Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases.md)です。  
  
> [!IMPORTANT]  
>  **資格情報名**引数は、名前がコンテナーのパスと一致する必要があります、先頭は https、および、末尾にスラッシュが含まれていません。 **IDENTITY**引数には、名前が必要です*SHARED ACCESS SIGNATURE*です。 **シークレット**引数には、共有アクセス署名トークンが必要です。  
  
```  
USE master  
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.  
   WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
   , SECRET = 'sharedaccesssignature' –- this is the shared access signature token   
GO    
```  
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER CREDENTIAL &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-credential-transact-sql.md)   
 [資格情報 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-credential-transact-sql.md)   
 [データベース スコープの資格情報 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [レッスン 2: 共有アクセス署名を使用して SQL Server 資格情報を作成します。](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)   
 [共有アクセス署名](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
  
  
