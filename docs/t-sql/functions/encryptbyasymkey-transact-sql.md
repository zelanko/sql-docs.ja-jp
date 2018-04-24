---
title: ENCRYPTBYASYMKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYASYMKEY
- ENCRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYASYMKEY function
- encryption [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], ENCRYPTBYASYMKEY function
ms.assetid: 86bb2588-ab13-4db2-8f3c-42c9f572a67b
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff79a5a15cb293646d75d4a411632f58c3efe0de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="encryptbyasymkey-transact-sql"></a>ENCRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  非対称キーでデータを暗号化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EncryptByAsymKey ( Asym_Key_ID , { 'plaintext' | @plaintext } )  
```  
  
## <a name="arguments"></a>引数  
 *Asym_Key_ID*  
 データベース内の非対称キーの ID を指定します。 **int**.  
  
 *cleartext*  
 非対称キーで暗号化するデータの文字列を指定します。  
  
 **@plaintext**  
 非同期キーを使用して暗号化されるデータを含む **nvarchar**、**char**、**varchar**、**binary**、**varbinary**、または **nchar** 型の変数を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>Remarks  
 非対称キーでの暗号化および暗号化解除は、対称キーの場合に比べて非常に時間がかかります。 テーブル内のユーザー データなど、大きなデータセットは、非対称キーを使用して暗号化しないことをお勧めします。 代わりに、強力な対称キーを使用してデータを暗号化し、非対称キーを使用してその対称キーを暗号化してください。  
  
 **EncryptByAsymKey** 返す **NULL** 場合は、入力は、アルゴリズムによっては、バイト数を超えています。 この上限は、次のとおりです。512 ビットの RSA キーでは、最大 53 バイトを暗号化できます。1024 ビットのキーでは、最大 117 バイトを暗号化できます。2048 ビットのキーでは、最大 245 バイトを暗号化できます  ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、証明書と非対称キーはどちらも RSA キーのラッパーです)。  
  
## <a name="examples"></a>使用例  
 次の例では、`@cleartext` に格納されているテキストを非対称キー `JanainaAsymKey02` を使用して暗号化します。 暗号化したデータは、`ProtectedData04` テーブルに挿入します。  
  
```  
INSERT INTO AdventureWorks2012.Sales.ProtectedData04   
    VALUES( N'Data encrypted by asymmetric key ''JanainaAsymKey02''',  
    EncryptByAsymKey(AsymKey_ID('JanainaAsymKey02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DECRYPTBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
