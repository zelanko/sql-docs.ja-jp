---
title: "ENCRYPTBYKEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYKEY_TSQL
- ENCRYPTBYKEY
dev_langs:
- TSQL
helpviewer_keywords:
- authenticators [SQL Server]
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], ENCRYPTBYKEY function
- ENCRYPTBYKEY function
ms.assetid: 0e11f8c5-f79d-46c1-ab11-b68ef05d6787
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b9b4aea4916cfb74efbead6d06c830698a4167
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="encryptbykey-transact-sql"></a>ENCRYPTBYKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  対称キーを使用してデータを暗号化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EncryptByKey ( key_GUID , { 'cleartext' | @cleartext }  
    [, { add_authenticator | @add_authenticator }  
     , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>引数  
 *key_GUID*  
 暗号化に使用するキーの GUID、*クリアテキスト*です。 **uniqueidentifier**です。  
  
 '*クリアテキスト*'  
 キーで暗号化されるデータを指定します。  
  
 @cleartext  
 型の変数は、 **nvarchar**、 **char**、 **varchar**、**バイナリ**、 **varbinary**、または**nchar**キーで暗号化されているデータが含まれます。  
  
 *add_authenticator*  
 と共に認証子を暗号化するかどうかを*クリアテキスト*です。 認証子を使用する場合は 1 にする必要があります。 **int**です。  
  
 @add_authenticator  
 と共に認証子を暗号化するかどうかを*クリアテキスト*です。 認証子を使用する場合は 1 にする必要があります。 **int**です。  
  
 *認証子*  
 認証子の派生元のデータを指定します。 **sysname**です。  
  
 @authenticator  
 認証子の派生元のデータを含む変数を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
 キーが開かれていない場合、キーが存在しない場合、またはキーが非推奨の RC4 キーでデータベースの互換性レベルが 110 以上の場合、NULL を返します。  
  
## <a name="remarks"></a>解説  
 EncryptByKey では対称キーが使用されます。 このキーは開いている必要があります。 対称キーが現在のセッションで既に開いている場合、クエリのコンテキストで再度開く必要はありません。  
  
 認証子を使用すると、暗号化されたフィールド全体が外部から置き換えられるのを防ぐことができます。 次の給与データの表を例として説明します。  
  
|従業員 ID (Employee_ID)|役職 (Standard_Title)|基本給 (Base_Pay)|  
|------------------|---------------------|---------------|  
|345|事務アシスタント|Fskj%7^edhn00|  
|697|最高財務責任者|M0x8900f56543|  
|694|データ入力主任|Cvc97824%^34f|  
  
 暗号を破らなくても、暗号文が格納された前後関係から悪意のあるユーザーは重要な情報を推測できます。 最高財務責任者は事務アシスタントよりも給与が多いので、"M0x8900f56543" として暗号化された値は、"Fskj%7^edhn00" として暗号化された値よりも大きくなります。 この場合、テーブルの ALTER 権限を持つユーザーが、最高財務責任者の Base_Pay フィールドに格納されたデータをコピーして、この事務アシスタントの Base_Pay フィールドと置き換えれば、給与を上げることができます。 この、値全体を置き換えてしまう攻撃は、データが暗号化されていても行うことができます。  
  
 値全体の置き換え攻撃を阻止するには、プレーン テキストを暗号化する前にコンテキスト情報を追加します。 このコンテキスト情報を使用すると、プレーン テキストのデータが移動されていないことを検証できます。  
  
 データを暗号化するときに認証子のパラメーターを指定した場合、DecryptByKey を使用してデータの暗号化を解除するときに同じ認証子が必要になります。 暗号化のとき、認証子のハッシュをプレーン テキストと共に暗号化します。 暗号化を解除するときには、同じ認証子が DecryptByKey に渡される必要があります。 2 つの認証子が一致しない場合、暗号化は解除できません。 これは、値が暗号化の後で移動されたことを示します。 一意で不変の値を含む列を認証子として使用することをお勧めします。 認証子の値が変更された場合、データへのアクセスが失われることがあります。  
  
 対称キーの暗号化と暗号化解除は比較的高速なので、データが大きい場合に適しています。  
  
> [!IMPORTANT]  
>  使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ANSI_PADDING OFF 設定と共に暗号化関数には暗黙的な変換によってデータが失われる可能性があります。 ANSI_PADDING の詳細については、次を参照してください。 [SET ANSI_PADDING & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
## <a name="examples"></a>使用例  
 キーに基づいて、次の例に示すように機能し、証明書を作成[操作方法: 列のデータを暗号化](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)です。  
  
### <a name="a-encrypting-a-string-with-a-symmetric-key"></a>A. 対称キーで文字列を暗号化する  
 次の例では、`Employee` テーブルに列を追加した後、`NationalIDNumber` 列に格納された社会保障番号の値を暗号化します。  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Create a column in which to store the encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
GO  
  
-- Open the symmetric key with which to encrypt the data.  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
  
-- Encrypt the value in column NationalIDNumber with symmetric key  
-- SSN_Key_01. Save the result in column EncryptedNationalIDNumber.  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
```  
  
### <a name="b-encrypting-a-record-together-with-an-authentication-value"></a>B. レコードを認証値と共に暗号化する  
  
```  
USE AdventureWorks2012;  
  
-- Create a column in which to store the encrypted data.  
ALTER TABLE Sales.CreditCard.   
    ADD CardNumber_Encrypted varbinary(128);   
GO  
  
-- Open the symmetric key with which to encrypt the data.  
OPEN SYMMETRIC KEY CreditCards_Key11  
    DECRYPTION BY CERTIFICATE Sales09;  
  
-- Encrypt the value in column CardNumber with symmetric   
-- key CreditCards_Key11.  
-- Save the result in column CardNumber_Encrypted.    
UPDATE Sales.CreditCard  
SET CardNumber_Encrypted = EncryptByKey(Key_GUID('CreditCards_Key11'),   
    CardNumber, 1, CONVERT( varbinary, CreditCardID) );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DECRYPTBYKEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [HASHBYTES & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/hashbytes-transact-sql.md)  
  
  

