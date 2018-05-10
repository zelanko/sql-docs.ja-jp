---
title: CREATE COLUMN MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: e5dafed981c030b5f06e41610fd3add6c4af0238
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  データベースに列マスター キー メタデータ オブジェクトを作成します。 キーを表す列マスター キー メタデータ エントリ。外部キー ストアに格納され、[Always Encrypted &#40;Database Engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) 機能を使うときに列暗号化キーを保護 (暗号化) するために使われます。 複数の列マスター キーは、キーのローテーション、つまりセキュリティ強化のためのキーの定期的な変更に対応します。 列マスター キーは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または PowerShell のオブジェクト エクスプローラーを使って、キー ストアおよびそれに対応するデータベース内のメタデータ オブジェクトに作成できます。 詳しくは、「[Always Encrypted のキー管理の概要](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)」をご覧ください。  
  
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
  
 Always Encrypted が有効なクライアント ドライバー ライブラリには、一般的なキー ストア用のキー ストア プロバイダーが含まれます。   
  
使用可能なプロバイダーのセットは、クライアント ドライバーの種類とバージョンによって異なります。 特定のドライバーについては、Always Encrypted の次のドキュメントをご覧ください。

[Always Encrypted と .NET Framework Provider for SQL Server を使用してアプリケーションを開発する](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


下の表は、システム プロバイダーの名前です。  
  
|キー格納プロバイダー名|格納されているキーを基になります。|  
    |-----------------------------|--------------------------|
    |' MSSQL_CERTIFICATE_STORE'|Windows 証明書ストア| 
    |' MSSQL_CSP_PROVIDER'|Microsoft CryptoAPI をサポートするハードウェア セキュリティ モジュール (HSM) などのストアです。|
    |' MSSQL_CNG_STORE'|Cryptography API をサポートするハードウェア セキュリティ モジュール (HSM) などのストアにします。 次世代です。|  
    |'Azure_Key_Vault'|「[Azure Key Vault の使用を開始する](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)」をご覧ください|  
  

 カスタム キー ストア プロバイダーを実装して、Always Encrypted が有効なクライアント ドライバーに組み込みのキー ストア プロバイダーがないストアに列マスター キーを格納できます。  カスタム キー ストア プロバイダーの名前を "MSSQL_" で始めることはできないことに注意してください。これは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] キー ストア プロバイダー用に予約されているプレフィックスです。 

  
 key_path  
 列のマスター_キーにキーのパスを格納します。 キーのパスを暗号化または (間接的に)、参照されている列のマスター_キーで保護されて、列に格納されたデータを復号化に想定される各クライアント アプリケーションのコンテキストで有効にする必要があり、クライアント アプリケーションは、キーへのアクセスを許可する必要があります。 キーのパスの形式は、キー格納プロバイダーに固有です。 次の一覧では、特定の Microsoft システム キー ストア プロバイダーのキー パスの形式を説明します。  
  
-   **プロバイダー名:** MSSQL_CERTIFICATE_STORE  
  
     **キー パスの形式:** *CertificateStoreName*/*CertificateStoreLocation*/*CertificateThumbprint*  
  
     各要素の説明は次のとおりです。  
  
     *CertificateStoreLocation*  
     証明書ストアの場所。現在のユーザーまたはローカル マシンにする必要があります。 詳しくは、「[Local Machine and Current User Certificate Stores](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx)」(ローカル マシンおよび現在のユーザーの証明書ストア) をご覧ください。  
  
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
     暗号サービス プロバイダー (CSP) の名前。列マスター キー ストアの場合は、CAPI を実装しています。 キー ストアとして HSM を使う場合は、HSM ベンダー提供の CSP の名前にする必要があります。 クライアント コンピューターでは、プロバイダーをインストールする必要があります。  
  
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
     キー ストレージ プロバイダー (KSP) の名前。列マスター キー ストアの場合、Cryptography: Next Generation (CNG) API を実装しています。 キー ストアとして HSM を使う場合は、HSM ベンダー提供の KSP の名前にする必要があります。 プロバイダーでは、クライアント コンピューターにインストールする必要があります。  
  
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
  
## <a name="remarks"></a>Remarks  

データベースに暗号化キー メタデータ エントリを作成する前、および Always Encrypted を使ってデータベース内の列を暗号化する前に、列マスター キー メタデータ エントリを作成する必要があります。 メタデータ内の列マスター キー エントリには実際の列マスター キーは含まれないことに注意してください。実際の列マスター キーは、外部の列キー ストア (SQL Server の外部) に格納する必要があります。 キー ストア プロバイダー名と、メタデータで列のマスター_キーのパスは、列のマスター_キーで暗号化された列の暗号化キーの暗号化を解除して、暗号化された列をクエリに列のマスター_キーを使用することができるクライアント アプリケーションに対して有効である必要があります。


  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY COLUMN MASTER KEY** 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-column-master-key"></a>A. 列のマスター_キーを作成します。  
 MSSQL_CERTIFICATE_STORE プロバイダーを使って列マスター キーにアクセスするクライアント アプリケーションの場合の、証明書ストアに格納される列マスター キーの列マスター キー メタデータ エントリの作成:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 MSSQL_CNG_STORE プロバイダーを使うクライアント アプリケーションによってアクセスされる列マスター キーの列マスター キー メタデータ エントリの作成:  
  
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
 
* [DROP COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Always Encrypted のキー管理の概要](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  
