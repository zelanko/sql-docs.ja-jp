---
title: DECRYPTBYKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DecryptByKey_TSQL
- DECRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], DecryptByKey function
- decryption [SQL Server], keys
- decryption [SQL Server], symmetric keys
- DECRYPTBYKEY function
ms.assetid: 6edf121f-ac62-4dae-90e6-6938f32603c9
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7f9e1e678fba7a2b2d24a85f4d57f1112b3d4cb8
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779478"
---
# <a name="decryptbykey-transact-sql"></a>DECRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

この関数は対称キーを使用してデータを復号します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DecryptByKey ( { 'ciphertext' | @ciphertext }   
    [ , add_authenticator, { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>引数  
*ciphertext*  
キーで暗号化されたデータを含む、型 **varbinary** の変数。  
  
**@ciphertext**  
キーで暗号化されたデータを含む、型 **varbinary** の変数。  
  
 *add_authenticator*  
元の暗号化プロセスにプレーンテキストと共に認証子が含まれ、認証子が暗号化されたかどうかを示します。 データ暗号化プロセス中、[ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) に渡された値に一致する必要があります。 *add_authenticator* には、**int** データ型が与えられます。  
  
 *authenticator*  
認証子の生成の基礎として使用されるデータ。 [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) に与えられた値と一致する必要があります。 *authenticator* には、**sysname** データ型が与えられます。  

**@authenticator**  
認証子の生成元となるデータを含む変数。 [ENCRYPTBYKEY (Transact-SQL)](./encryptbykey-transact-sql.md) に与えられた値と一致する必要があります。 *@authenticator* には、**sysname** データ型が与えられます。  

## <a name="return-types"></a>戻り値の型  
最大サイズが 8,000 バイトの **varbinary**。 `DECRYPTBYKEY` は、データの暗号化に使用する対称キーが開いていない場合か、*ciphertext* が NULL の場合、NULL を返します。  
  
## <a name="remarks"></a>Remarks  
`DECRYPTBYKEY` は対称キーを使用します。 データベースでは、この対称キーを既に開いている必要があります。 `DECRYPTBYKEY` では、複数のキーを同時に開いておくことができます。 暗号化テキストの復号する直前にキーを開く必要はありません。  
  
対称暗号化/復号は通常、比較的すぐに動作します。大量のデータが含まれる操作で効率的に動作します。  
  
## <a name="permissions"></a>アクセス許可  
対称キーは現在のセッションで開かれている必要があります。 詳細については、「[OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-decrypting-by-using-a-symmetric-key"></a>A. 対称キーを使用して暗号化解除する  
この例では、対称キーで暗号化テキストを復号します。  
  
```  
-- First, open the symmetric key with which to decrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
GO  
  
-- Now list the original ID, the encrypted ID, and the   
-- decrypted ciphertext. If the decryption worked, the original  
-- and the decrypted ID will match.  
SELECT NationalIDNumber, EncryptedNationalID   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalID))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
GO  
```  
  
### <a name="b-decrypting-by-using-a-symmetric-key-and-an-authenticating-hash"></a>B. 対称キーと認証ハッシュを使用して暗号化解除する  
この例では、認証子と共に、最初に暗号化されたデータを復号します。  
  
```  
-- First, open the symmetric key with which to decrypt the data  
OPEN SYMMETRIC KEY CreditCards_Key11  
   DECRYPTION BY CERTIFICATE Sales09;  
GO  
  
-- Now list the original card number, the encrypted card number,  
-- and the decrypted ciphertext. If the decryption worked,   
-- the original number will match the decrypted number.  
SELECT CardNumber, CardNumber_Encrypted   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByKey(CardNumber_Encrypted, 1 ,   
    HashBytes('SHA1', CONVERT(varbinary, CreditCardID))))   
    AS 'Decrypted card number' FROM Sales.CreditCard;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
  
