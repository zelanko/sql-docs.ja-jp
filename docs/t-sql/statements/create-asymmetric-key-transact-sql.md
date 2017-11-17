---
title: "非対称キー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
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
- ASYMMETRIC_KEY_TSQL
- CREATE ASYMMETRIC KEY
- CREATE_ASYMMETRIC_KEY_TSQL
- ASYMMETRIC KEY
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], creating
- encryption [SQL Server], asymmetric keys
- CREATE ASYMMETRIC KEY statement
- asymmetric keys [SQL Server]
- cryptography [SQL Server], asymmetric keys
ms.assetid: 141bc976-7631-49f6-82bd-a235028645b1
caps.latest.revision: 51
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f39a31a9b2de4cd8153fa617b9cab1c1235f2a7a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-asymmetric-key-transact-sql"></a>CREATE ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベースに非対称キーを作成します。  
  
 この機能は、データ層アプリケーション フレームワーク (DACFx) を使用してデータベースのエクスポートとの互換性はありません。 エクスポートする前に、すべての非対称キーを削除する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE ASYMMETRIC KEY Asym_Key_Name   
   [ AUTHORIZATION database_principal_name ]  
   [ FROM <Asym_Key_Source> ]  
   [ WITH <key_option> ] 
   [ ENCRYPTION BY <encrypting_mechanism> ] 
   [ ; ]
  
<Asym_Key_Source>::=  
     FILE = 'path_to_strong-name_file'  
   | EXECUTABLE FILE = 'path_to_executable_file'  
   | ASSEMBLY Assembly_Name  
   | PROVIDER Provider_Name  
  
<key_option> ::=  
   ALGORITHM = <algorithm>  
      |  
   PROVIDER_KEY_NAME = 'key_name_in_provider'  
      |  
      CREATION_DISPOSITION = { CREATE_NEW | OPEN_EXISTING }  
  
<algorithm> ::=  
      { RSA_4096 | RSA_3072 | RSA_2048 | RSA_1024 | RSA_512 }   
  
<encrypting_mechanism> ::=  
    PASSWORD = 'password'   
```  
  
## <a name="arguments"></a>引数  
 *Asym_Key_Source*  
 非対称キー ペアの読み込み元を指定します。  
  
 承認*database_principal_name*  
 非対称キーの所有者を指定します。 所有者にロールとグループは指定できません。 このオプションを省略した場合、所有者は現在のユーザーになります。  
  
 ファイル ='*path_to_strong name_file*'  
 キー ペアの読み込み元となる、厳密な名前のファイルのパスを指定します。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 実行可能ファイル ='*path_to_executable_file*'  
 公開キーの読み込み元となる、アセンブリ ファイルを指定します。 Windows API の MAX_PATH による 260 文字までの制限があります。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 アセンブリ*アセンブリ名*  
 公開キーの読み込み元となる、アセンブリの名前を指定します。  
  
ENCRYPTION BY  *\<key_name_in_provider >*キーの暗号化方法を指定します。 証明書、パスワード、または非対称キーを指定できます。  
  
 KEY_NAME ='*key_name_in_provider*'  
 外部プロバイダーからキー名を指定します。 外部キー管理の詳細については、次を参照してください。[拡張キー管理 & #40 です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 CREATION_DISPOSITION = CREATE_NEW  
 拡張キー管理デバイス上で新しいキーを作成します。 デバイス上のキー名を指定するには、PROV_KEY_NAME を使用する必要があります。 デバイスでキーが既に存在する場合、ステートメントはエラーで失敗します。  
  
 CREATION_DISPOSITION = OPEN_EXISTING  
 マップ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称のキーを既存の拡張キー管理キー。 デバイス上のキー名を指定するには、PROV_KEY_NAME を使用する必要があります。 CREATION_DISPOSITION = OPEN_EXISTING が指定されない場合、既定値は CREATE_NEW です。  
  
 アルゴリズム =\<アルゴリズム >  
 5 つのアルゴリズムを指定することができます。RSA_4096、RSA_3072、RSA_2048、RSA_1024、および RSA_512 です。  
  
 RSA_1024 と RSA_512 が推奨されていません。 RSA_1024 または RSA_512 (推奨されません) を使用する 120 以下をデータベース互換性レベルを設定する必要があります。  
  
 パスワード = '*パスワード*'  
 秘密キーを暗号化するパスワードを指定します。 この句がない場合、秘密キーはデータベースのマスター キーで暗号化されます。 *パスワード*は最大 128 文字です。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="remarks"></a>解説  
 *非対称キー*は、データベース レベルのセキュリティ保護可能なエンティティです。 既定の形式では、このエンティティには公開キーと秘密キーの両方が含まれます。 FROM 句を使用せずに CREATE ASYMMETRIC KEY を実行した場合は、新しいキー ペアが作成されます。 FROM 句を使用して CREATE ASYMMETRIC KEY を実行した場合は、キー ペアがファイルからインポートされるか、公開キーがアセンブリからインポートされます。  
  
 既定では、秘密キーはデータベースのマスター キーによって保護されます。 データベースのマスター キーが作成されていない場合、秘密キーを保護するにはパスワードが必要です。 データベースのマスター キーが存在する場合、パスワードは省略可能です。  
  
 秘密キーは、512、1,024、または 2,048 ビットの長さで指定できます。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CREATE ASYMMETRIC KEY 権限が必要です。 AUTHORIZATION 句を指定する場合は、データベース プリンシパルに対する IMPERSONATE 権限、またはアプリケーション ロールに対する ALTER 権限が必要です。 Windows のログインのみに使用する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、およびアプリケーション ロールは、非対称キーを所有できます。 グループとロールは非対称キーを所有できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-an-asymmetric-key"></a>A. 非対称キーを作成する  
 という名前の非対称キーを作成する例を次`PacificSales09`を使用して、`RSA_2048`アルゴリズム、およびパスワードで秘密キーを保護します。  
  
```  
CREATE ASYMMETRIC KEY PacificSales09   
    WITH ALGORITHM = RSA_2048   
    ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';   
GO  
```  
  
### <a name="b-creating-an-asymmetric-key-from-a-file-giving-authorization-to-a-user"></a>B. 非対称キーをファイルから作成し、ユーザーを認証する  
 次の例では、ファイルに格納されたキー ペアから非対称キー `PacificSales19` を作成し、ユーザー `Christina` がその非対称キーを使用することを承認します。  
  
```  
CREATE ASYMMETRIC KEY PacificSales19 AUTHORIZATION Christina   
    FROM FILE = 'c:\PacSales\Managers\ChristinaCerts.tmp'    
    ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="c-creating-an-asymmetric-key-from-an-ekm-provider"></a>C. EKM プロバイダーから非対称キーを作成する  
 次の例では、ファイルに格納されたキー ペアから非対称キー `EKM_askey1` を作成します。 暗号化と呼ばれる拡張キー管理プロバイダーを使用して`EKMProvider1`、し、そのプロバイダーは、キーと呼ばれる`key10_user1`です。  
  
```  
CREATE ASYMMETRIC KEY EKM_askey1   
    FROM PROVIDER EKM_Provider1  
    WITH   
        ALGORITHM = RSA_2048,   
        CREATION_DISPOSITION = CREATE_NEW  
        , PROVIDER_KEY_NAME  = 'key10_user1' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Azure Key Vault を使用する拡張キー管理 &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
  

