---
title: "SIGNBYCERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SIGNBYCERT
- SIGNBYCERT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- text signing [SQL Server]
- encryption [SQL Server], certificates
- certificates [SQL Server], text signing
- SignByCert function
- signing text [SQL Server]
- SIGNBYCERT function
- cryptography [SQL Server], certificates
ms.assetid: b4c6bced-4473-4bae-85b9-56deced495f9
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd5940957c3a75555db9032097a99f73639f89bb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="signbycert-transact-sql"></a>SIGNBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  証明書を使用してテキストに署名し、その署名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SignByCert ( certificate_ID , @cleartext [ , 'password' ] )  
```  
  
## <a name="arguments"></a>引数  
 *certificate_ID*  
 データベースに含まれる証明書の ID を指定します。 *certificate_ID*は**int**です。  
  
 *@cleartext*  
 型の変数は、 **nvarchar**、 **char**、 **varchar**、または**nchar**が署名されるデータを格納します。  
  
 **'** *パスワード* **'**  
 証明書の秘密キーを暗号化する場合に使用したパスワードを指定します。 *パスワード*は**nvarchar (128)**です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>解説  
 証明書に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、テキストをサインイン`@SensitiveData`証明書で`ABerglundCert07`、暗号化解除パスワード"pGFD4bb925DGvbd2439587y"を持つ証明書。 その後、クリアテキストと署名をテーブル `SignedData04` に挿入します。  
  
```  
DECLARE @SensitiveData nvarchar(max);  
SET @SensitiveData = N'Saddle Price Points are   
    2, 3, 5, 7, 11, 13, 17, 19, 23, 29';  
INSERT INTO [SignedData04]  
    VALUES( N'data signed by certificate ''ABerglundCert07''',  
    @SensitiveData, SignByCert( Cert_Id( 'ABerglundCert07' ),   
    @SensitiveData, N'pGFD4bb925DGvbd2439587y' ));  
GO  
```  
  
## <a name="see-also"></a>参照  
 [VERIFYSIGNEDBYCERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/verifysignedbycert-transact-sql.md)   
 [CERT_ID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cert-id-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [証明書 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
