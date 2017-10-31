---
title: "DECRYPTBYKEYAUTOCERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/09/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0842000cd08e3ca82dab181f32ae96f4a0280d5d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  証明書で自動的に暗号化解除された対称キーを使用し、暗号化を解除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## 構文  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## 引数  
 *cert_ID*  
 対称キーの保護に使用されている証明書の ID です。 *cert_ID*は**int**です。  
  
 *cert_password*  
 証明書の秘密キーを保護するパスワードを指定します。 秘密キーがデータベースのマスター キーで保護されている場合は NULL を指定できます。 *cert_password*は**nvarchar**です。  
  
 '*暗号化テキスト*'  
 キーで暗号化されたデータです。 *暗号化テキスト*は**varbinary**です。  
  
 @ciphertext  
 型の変数は、 **varbinary**キーで暗号化されたデータが含まれます。  
  
 *add_authenticator*  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 データを暗号化するときに EncryptByKey に渡されたものと同じ値にする必要があります。**1**認証子が使用された場合。 *add_authenticator*は**int**です。  
  
 @add_authenticator  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 データを暗号化する際に EncryptByKey に渡された値と同じである必要があります。  
  
 *認証子*  
 認証子の生成元のデータを指定します。 EncryptByKey に渡された値と一致する必要があります。 *認証子*は**sysname**です。  
  
 @authenticator  
 認証子の生成元のデータを含む変数を指定します。 EncryptByKey に渡された値と一致する必要があります。  
  
## 戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## 解説  
 DecryptByKeyAutoCert は、OPEN SYMMETRIC KEY および DecryptByKey の機能を組み合わせたもので、 対称キーの暗号化解除と、そのキーを使用した暗号化テキストの暗号化解除を 1 回の操作で行います。  
  
## Permissions  
 対称キーに対する VIEW DEFINITION 権限と、証明書に対する CONTROL 権限が必要です。  
  
## 使用例  
 例を次にどのように`DecryptByKeyAutoCert`を復号化を実行するコードを簡略化するために使用できます。 このコードを実行する必要があります、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース マスター _ キーを既には持たないデータベース。  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE CERTIFICATE HumanResources037   
   WITH SUBJECT = 'Sammamish HR',   
   EXPIRY_DATE = '10/31/2009';  
CREATE SYMMETRIC KEY SSN_Key_01 WITH ALGORITHM = DES  
    ENCRYPTION BY CERTIFICATE HumanResources037;  
GO  
----Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037 ;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
--  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key  
--2. Decrypt the data  
--3. Close the symmetric key  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
SELECT NationalIDNumber, EncryptedNationalIDNumber    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--OPTION TWO, using DecryptByKeyAutoCert()  
SELECT NationalIDNumber, EncryptedNationalIDNumber   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoCert ( cert_ID('HumanResources037') , NULL ,EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
```  
  
## 参照  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

