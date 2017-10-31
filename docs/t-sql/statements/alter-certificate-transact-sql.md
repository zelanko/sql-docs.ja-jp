---
title: "ALTER CERTIFICATE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_CERTIFICATE_TSQL
- ALTER CERTIFICATE
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTION BY PASSWORD option
- encryption [SQL Server], certificates
- modifying certificates
- private keys [SQL Server]
- ALTER CERTIFICATE statement
- certificates [SQL Server], modifying
ms.assetid: da4dc25e-72e0-4036-87ce-22de83160836
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: da51e41cc5adf4fa9f4f57cfe094fe5a72119c70
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="alter-certificate-transact-sql"></a>ALTER CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  証明書を暗号化するときに使用する秘密キーを変更します。秘密キーが存在しない場合は追加します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] に対して、証明書を使用できるようにするかどうかを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER CERTIFICATE certificate_name   
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY ( <private_key_spec> [ ,... ] )  
    | WITH ACTIVE FOR BEGIN_DIALOG = [ ON | OFF ]  
  
<private_key_spec> ::=   
      FILE = 'path_to_private_key'   
    | DECRYPTION BY PASSWORD = 'key_password'   
    | ENCRYPTION BY PASSWORD = 'password'   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER CERTIFICATE certificate_name   
{  
      REMOVE PRIVATE KEY  
    | WITH PRIVATE KEY (   
        FILE = '<path_to_private_key>',  
        DECRYPTION BY PASSWORD = '<key password>' )
}  
```  
  
## <a name="arguments"></a>引数  
 *certificate_name*  
 データベースで証明書を認識する一意の名前です。  
  
 ファイル**='***path_to_private_key***'**  
 秘密キーへの完全なパスを、ファイル名を含めて指定します。 このパラメーターには、ローカル パスまたはネットワーク上の場所を示す UNC パスを指定できます。 このファイルには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストでアクセスします。 このオプションを使用するときには、サービス アカウントに、指定したファイルへのアクセス権があることを確認する必要があります。  
  
 DECRYPTION BY PASSWORD **='***key_password***'**  
 秘密キーの暗号化解除に必要なパスワードを指定します。  
  
 ENCRYPTION BY PASSWORD **='***パスワード***'**  
 データベース内の証明書の秘密キーを暗号化するために使用されるパスワードを指定します。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、「 [Password Policy](../../relational-databases/security/password-policy.md)」をご参照ください。  
  
 REMOVE PRIVATE KEY  
 秘密キーをデータベース内で保持しないよう指定します。  
  
 ACTIVE FOR BEGIN_DIALOG  **=**  {ON |オフ}  
 発信側に証明書を使用できるように、[!INCLUDE[ssSB](../../includes/sssb-md.md)]ダイアログ メッセージ交換します。  
  
## <a name="remarks"></a>解説  
 秘密キーがで指定されたパブリック キーに対応する必要があります*certificate_name*です。  
  
 DECRYPTION BY PASSWORD 句は、ファイル内のパスワードが NULL パスワードで保護されている場合は省略できます。  
  
 データベースに既に存在する証明書の秘密キーをファイルからインポートするとき、その秘密キーはデータベース マスター キーにより自動的に保護されます。 秘密キーをパスワードで保護するには、ENCRYPTION BY PASSWORD 句を使用します。  
  
 REMOVE PRIVATE KEY オプションを指定すると、データベースから証明書の秘密キーが削除されます。 これを行う証明書は署名の検証に使用するときまたは[!INCLUDE[ssSB](../../includes/sssb-md.md)]秘密キーを必要としないシナリオです。 対称キーを保護する証明書の秘密キーを削除しないでください。  
  
 秘密キーがデータベース マスター キーを使って暗号化される場合は、暗号化解除のパスワードを指定する必要はありません。  
  
> [!IMPORTANT]  
>  データベースから秘密キーを削除する前には、必ず秘密キーの保存用コピーを作成してください。 詳細については、「[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)」を参照してください。  
  
 WITH PRIVATE KEY オプションは、包含データベースでは使用できません。  
  
## <a name="permissions"></a>Permissions  
 証明書に対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-password-of-a-certificate"></a>A. 証明書のパスワードを変更する  
  
```  
ALTER CERTIFICATE Shipping04   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = 'pGF$5DGvbd2439587y',  
    ENCRYPTION BY PASSWORD = '4-329578thlkajdshglXCSgf');  
GO  
```  
  
### <a name="b-changing-the-password-that-is-used-to-encrypt-the-private-key"></a>B. 秘密キーの暗号化に使用するパスワードを変更する  
  
```  
ALTER CERTIFICATE Shipping11   
    WITH PRIVATE KEY (ENCRYPTION BY PASSWORD = '34958tosdgfkh##38',  
    DECRYPTION BY PASSWORD = '95hkjdskghFDGGG4%');  
GO  
```  
  
### <a name="c-importing-a-private-key-for-a-certificate-that-is-already-present-in-the-database"></a>C. データベースに存在する証明書の秘密キーをインポートする  
  
```  
ALTER CERTIFICATE Shipping13   
    WITH PRIVATE KEY (FILE = 'c:\\importedkeys\Shipping13',  
    DECRYPTION BY PASSWORD = 'GDFLKl8^^GGG4000%');  
GO  
```  
  
### <a name="d-changing-the-protection-of-the-private-key-from-a-password-to-the-database-master-key"></a>D. 秘密キーの保護をパスワードからデータベース マスター キーに変更する  
  
```  
ALTER CERTIFICATE Shipping15   
    WITH PRIVATE KEY (DECRYPTION BY PASSWORD = '95hk000eEnvjkjy#F%');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [証明書 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


