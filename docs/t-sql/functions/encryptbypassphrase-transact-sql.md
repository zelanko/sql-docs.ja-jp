---
title: "ENCRYPTBYPASSPHRASE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYPASSPHRASE
- ENCRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYPASSPHRASE function
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], ENCRYPTBYPASSPHRASE function
ms.assetid: f8dbb9e6-94d6-40d7-8b38-6833a409d597
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ddfbea4ac550f21787eb88db6119c391f2b1b85a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="encryptbypassphrase-transact-sql"></a>ENCRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  キーの長さが 128 ビットの TRIPLE DES アルゴリズムを使用して、パスフレーズでデータを暗号化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EncryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'cleartext' | @cleartext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>引数  
 *パスフレーズ*  
 対称キーを生成するパスフレーズを指定します。  
  
 @passphrase  
 型の変数**nvarchar**、 **char**、 **varchar**、**バイナリ**、 **varbinary**、または**nchar**対称キーを生成するためのパスフレーズを含むです。  
  
 *クリア テキスト*  
 暗号化するクリア テキストを指定します。  
  
 @cleartext  
 型の変数**nvarchar**、 **char**、 **varchar**、**バイナリ**、 **varbinary**、または**nchar**クリア テキストです。 最大サイズは、8,000 バイトです。  
  
 *add_authenticator*  
 クリア テキストと共に認証子を暗号化するかどうかを指定します。 認証子を追加する場合は 1 を指定します。 **int**です。  
  
 @add_authenticator  
 クリア テキストと共にハッシュを暗号化するかどうかを指定します。  
  
 *認証子*  
 認証子の取得元となるデータを指定します。 **sysname**です。  
  
 @authenticator  
 認証子の取得元となるデータを含む変数を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズにします。  
  
## <a name="remarks"></a>解説  
 パス フレーズは空白を含むパスワードです。 パスフレーズを使用する利点は、比較的長い文字列を覚えるより、意味のある句やセンテンスを覚える方が簡単であるという点です。  
  
 この関数ではパスワードの複雑性はチェックされません。  
  
## <a name="examples"></a>使用例  
 次の例は、内のレコードを更新、`SalesCreditCard`テーブルし、列に格納されたクレジット_カード番号の値を暗号化`CardNumber_EncryptedbyPassphrase`、認証子として主キーを使用します。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create a column in which to store the encrypted data.  
ALTER TABLE Sales.CreditCard   
    ADD CardNumber_EncryptedbyPassphrase varbinary(256);   
GO  
-- First get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
    = 'A little learning is a dangerous thing!';  
  
-- Update the record for the user's credit card.  
-- In this case, the record is number 3681.  
UPDATE Sales.CreditCard  
SET CardNumber_EncryptedbyPassphrase = EncryptByPassPhrase(@PassphraseEnteredByUser  
    , CardNumber, 1, CONVERT( varbinary, CreditCardID))  
WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DECRYPTBYPASSPHRASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/decryptbypassphrase-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

