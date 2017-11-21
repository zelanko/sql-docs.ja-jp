---
title: "列のマスター _ キー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 871acb46898a9a62b25062f69d4e51bf28658f06
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  データベース内の列マスター キー メタデータ オブジェクトを作成します。 保護に使用される外部キー ストアに格納されている、キーを表す列マスター _ キーのメタデータ エントリ (暗号化) 列の暗号化キーを使用する場合、 [Always Encrypted & #40";"データベース エンジン"&"#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)機能します。 キーのローテーションに関して複数の列マスター _ キーを許可します。セキュリティを強化するためにキーを定期的に変更します。 オブジェクト エクスプ ローラーを使用してキー ストアと、データベース内の対応するメタデータ オブジェクトの列マスター _ キーを作成することができます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または PowerShell。 詳細については、「 [Always Encrypted のキー管理の概要](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
         )   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *key_name*  
 データベースで、列のマスター_キーを認識する名前です。  
  
 *key_store_provider_name*  
 列のマスター キーを含むキー ストアをカプセル化するクライアント側ソフトウェア コンポーネントであるキー ストア プロバイダーの名前を指定します。 常に暗号化が有効なクライアント ドライバーでは、格納されているキーのプロバイダー名を使用して、キー ストア プロバイダーのドライバーのレジストリに格納されているキーのプロバイダーを検索します。 ドライバーでは、基になるキー ストアに格納されている、列マスター_キーで保護されている、列の暗号化キーの暗号化を解除するのに、プロバイダーを使用します。 列の暗号化キーのプレーン テキストの値は、暗号化されたデータベースの列に対応する、クエリ パラメーターを暗号化または暗号化された列からのクエリ結果の暗号化を解除するには使用されます。  
  
 Always Encrypted が有効なクライアント ドライバー ライブラリには、一般的なキー ストアのキー ストア プロバイダーが含まれます。   
  
使用可能なプロバイダーのセットは、型と、クライアント ドライバーのバージョンによって異なります。 特定のドライバーの Always Encrypted のドキュメントを参照してください。

[使用して Always Encrypted と .NET Framework Provider for SQL Server アプリケーションを開発します。](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


下の表は、システム プロバイダーの名前をキャプチャします。  
  
|キー格納プロバイダー名|格納されているキーを基になります。|  
    |-----------------------------|--------------------------|
    |' MSSQL_CERTIFICATE_STORE'|Windows 証明書ストア| 
    |' MSSQL_CSP_PROVIDER'|Microsoft CryptoAPI をサポートするハードウェア セキュリティ モジュール (HSM) などのストアです。|
    |' MSSQL_CNG_STORE'|Cryptography API をサポートするハードウェア セキュリティ モジュール (HSM) などのストアにします。 次世代です。|  
    |' Azure_Key_Vault'|参照してください[Azure Key Vault の概要](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)|  
  

 カスタム キー ストア プロバイダーを実装する、格納するために対象の組み込みキーがない、ストア内の列マスター _ キー ストア プロバイダーは、Always Encrypted が有効なクライアント ドライバー。  用に予約されてカスタム キー ストア プロバイダーの名前が 'mssql _' では、プレフィックスで始まることはできません注[!INCLUDE[msCoName](../../includes/msconame-md.md)]キー ストア プロバイダー。 

  
 key_path  
 列のマスター_キーにキーのパスを格納します。 キーのパスを暗号化または (間接的に)、参照されている列のマスター_キーで保護されて、列に格納されたデータを復号化に想定される各クライアント アプリケーションのコンテキストで有効にする必要があり、クライアント アプリケーションは、キーへのアクセスを許可する必要があります。 キーのパスの形式は、キー格納プロバイダーに固有です。 次の一覧では、特定の Microsoft システム キー ストア プロバイダーのキーのパスの形式について説明します。  
  
-   **プロバイダー名:** MSSQL_CERTIFICATE_STORE  
  
     **キー パスの形式:** *証明*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     各要素の説明は次のとおりです。  
  
     *CertificateStoreLocation*  
     証明書ストアに、現在のユーザーまたはローカル コンピューターにする必要があります。 詳細については、次を参照してください。[ローカル マシンと現在のユーザー証明書ストア](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx)です。  
  
     *CertificateStore*  
     証明書ストアの名前、たとえば 'My' です。  
  
     *CertificateThumbprint*  
     証明書の拇印。  
  
     **使用例:**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **プロバイダー名:** MSSQL_CSP_PROVIDER  
  
     **キー パスの形式:** *ProviderName*/*KeyIdentifier*  
  
     各要素の説明は次のとおりです。  
  
     *ProviderName*  
     暗号化サービス プロバイダー (CSP)、CAPI を実装する、列マスター キー ストアの名前です。 HSM をキー ストアとして使用する場合、HSM ベンダーの CSP の名前でなければなりませんを提供します。 クライアント コンピューターでは、プロバイダーをインストールする必要があります。  
  
     *KeyIdentifier*  
     キーの識別子は、キーのストア内の列マスター_キーとして使用されます。  
  
     **使用例:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **プロバイダー名:** MSSQL_CNG_STORE  
  
     **キー パスの形式:** *ProviderName*/*KeyIdentifier*  
  
     各要素の説明は次のとおりです。  
  
     *ProviderName*  
     名前のキー格納プロバイダー (KSP)、暗号化を実装する: Next Generation (CNG) API、列マスター キー ストアにします。 KSP、HSM ベンダーの名前をあるこの必要があります、HSM をキー ストアとして使用する場合を提供します。 プロバイダーでは、クライアント コンピューターにインストールする必要があります。  
  
     *KeyIdentifier*  
     キーの識別子は、キーのストア内の列マスター_キーとして使用されます。  
  
     **使用例:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **プロバイダー名:** AZURE_KEY_STORE  
  
     **キー パスの形式:** *KeyUrl*  
  
     各要素の説明は次のとおりです。  
  
     *KeyUrl*  
     Azure Key Vault 内のキーの URL


例:
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>解説  

データベースと Always Encrypted を使用して、データベースの任意の列を暗号化する前に、列暗号化キーのメタデータ エントリを作成するには、この列のマスター _ キーのメタデータ エントリを作成することが必要です。 メタデータ内の列マスター _ キー エントリに、外部列のキー ストア (SQL Server) の外部に格納する必要がありますが、実際の列マスター _ キーが含まれていないことを注意してください。 キー ストア プロバイダー名と、メタデータで列のマスター_キーのパスは、列のマスター_キーで暗号化された列の暗号化キーの暗号化を解除して、暗号化された列をクエリに列のマスター_キーを使用することができるクライアント アプリケーションに対して有効である必要があります。


  
## <a name="permissions"></a>Permissions  
 必要があります、 **ALTER ANY COLUMN MASTER KEY**権限です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-column-master-key"></a>A. 列のマスター_キーを作成します。  
 MSSQL_CERTIFICATE_STORE プロバイダーを使用して、列マスター _ キーにアクセスするクライアント アプリケーションの証明書ストアに格納されている列マスター _ キーの列マスター _ キーのメタデータ エントリを作成しています。  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 MSSQL_CNG_STORE プロバイダーを使用するクライアント アプリケーションによってアクセスされる列マスター _ キーの列マスター _ キーのメタデータ エントリを作成しています。  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 プロバイダーを使用して、AZURE_KEY_VAULT、列のマスター_キーにアクセスするクライアント アプリケーションの場合、Azure のキー コンテナーに格納されている列マスター_キーを作成しています。  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 カスタムの列のマスター キー ストアに格納されている CMK を作成するには。  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>参照
 
* [列の MASTER KEY &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Always Encrypted のキー管理の概要](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  

