---
title: "ALTER SYMMETRIC KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- ALTER SYMMETRIC KEY
- ALTER_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- modifying symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], modifying
- cryptography [SQL Server], symmetric keys
- ALTER SYMMETRIC KEY statement
ms.assetid: d3c776a4-7d71-4e6f-84fc-1db47400c465
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 131fb5da53d4808836f94ee85f1c07134b98b626
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-symmetric-key-transact-sql"></a>ALTER SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  対称キーのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER SYMMETRIC KEY Key_name <alter_option>  
  
<alter_option> ::=  
   ADD ENCRYPTION BY <encrypting_mechanism> [ , ... n ]  
   |   
   DROP ENCRYPTION BY <encrypting_mechanism> [ , ... n ]  
<encrypting_mechanism> ::=  
   CERTIFICATE certificate_name  
   |  
   PASSWORD = 'password'  
   |  
   SYMMETRIC KEY Symmetric_Key_Name  
   |  
   ASYMMETRIC KEY Asym_Key_Name  
```  
  
## <a name="arguments"></a>引数  
 *Key_name*  
 変更する対称キーの、データベースで認識される名前を指定します。  
  
 ADD ENCRYPTION BY   
 指定の方法による暗号化を追加します。  
  
 DROP ENCRYPTION BY  
 指定の方法による暗号化を削除します。 対称キーからすべての暗号化を削除することはできません。  
  
 証明書*Certificate_name*  
 対称キーの暗号化に使用されている証明書を指定します。 この証明書はデータベース内に存在する必要があります。  
  
 パスワード**='***パスワード***'**  
 対称キーの暗号化に使用されるパスワードを指定します。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 対称キー *Symmetric_Key_Name*  
 変更する対称キーの暗号化に使用されている対称キーを指定します。 この対称キーはデータベースに存在し、開かれている必要があります。  
  
 非対称キー *Asym_Key_Name*  
 変更する対称キーの暗号化に使用されている非対称キーを指定します。 この非対称キーはデータベース内に存在する必要があります。  
  
## <a name="remarks"></a>解説  
  
> [!CAUTION]  
>  データベースのマスター キーの公開キーではなく、パスワードを使用して対称キーを暗号化する場合は、TRIPLE_DES 暗号化アルゴリズムが使用されます。 このため、AES など、強力な暗号化アルゴリズムで作成されたキーでも、キー自身はそれより弱いアルゴリズムで保護されます。  
  
 対称キーの暗号化を変更するには、ADD ENCRYPTION および DROP ENCRYPTION 句を使用します。 キーからすべての暗号化を削除することはできません。 このため、古い形式の暗号化を削除する前には、新しい形式の暗号化を追加してください。  
  
 対称キーの所有者を変更するには、使用[ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)です。  
  
> [!NOTE]  
>  RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。 データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます  (非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。  
  
## <a name="permissions"></a>Permissions  
 対称キーに対する ALTER 権限が必要です。 証明書または非対称キーを使って暗号化を追加する場合は、証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。 証明書または非対称キーを使って暗号化を削除する場合は、証明書または非対称キーに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、対称キーの保護に使用されている暗号化の方法を変更します。 対称キー `JanainaKey043` は、作成時に証明書 `Shipping04` を使用して暗号化されています。 暗号化なしでキーを格納することはできないため、この例では、パスワードによる暗号化を追加した後、証明書による暗号化を削除します。  
  
```  
CREATE SYMMETRIC KEY JanainaKey043 WITH ALGORITHM = AES_256   
    ENCRYPTION BY CERTIFICATE Shipping04;  
-- Open the key.   
OPEN SYMMETRIC KEY JanainaKey043 DECRYPTION BY CERTIFICATE Shipping04  
    WITH PASSWORD = '<enterStrongPasswordHere>';   
-- First, encrypt the key with a password.  
ALTER SYMMETRIC KEY JanainaKey043   
    ADD ENCRYPTION BY PASSWORD = '<enterStrongPasswordHere>';  
-- Now remove encryption by the certificate.  
ALTER SYMMETRIC KEY JanainaKey043   
    DROP ENCRYPTION BY CERTIFICATE Shipping04;  
CLOSE SYMMETRIC KEY JanainaKey043;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [CLOSE SYMMETRIC KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/close-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

