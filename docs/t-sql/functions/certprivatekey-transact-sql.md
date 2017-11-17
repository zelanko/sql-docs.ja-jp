---
title: "CERTPRIVATEKEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
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
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a44f9203f9242a8f90ce3ca667bc1fea479dc2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

証明書の秘密キーをバイナリ形式で返します。 この関数は 3 つの引数を受け取ります。
-   証明書の id。  
-   キーがクリア テキストでユーザーに公開されないように、秘密キーのビットが関数によって返されたときにそのビットを暗号化するために使用する暗号化パスワード。  
-   省略可能な暗号化解除パスワード。 暗号化解除パスワードを指定した場合は、そのパスワードを使用して、証明書の秘密キーの暗号化を解除します。それ以外の場合は、データベース マスター キーを使用します。  
  
この関数を使用できるのは、証明書の秘密キーにアクセスできるユーザーのみです。 この関数は、秘密キーを PVK 形式で返します。
  
## <a name="syntax"></a>構文  
  
```sql
CERTPRIVATEKEY   
    (  
          cert_ID   
        , ' encryption_password '   
      [ , ' decryption_password ' ]  
    )  
```  
  
## <a name="arguments"></a>引数  
*certificate_ID*  
**Certificate_id**証明書のです。 使用してまたは sys.certificates から使用できます。 これは、 [CERT_ID (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cert-id-transact-sql.md)関数。 *cert_id*は型です**int。**
  
*encryption_password*  
返されたバイナリ値の暗号化に使用するパスワード。
  
*decryption_password*  
返されたバイナリ値の暗号化の解除に使用するパスワード。
  
## <a name="return-types"></a>戻り値の型
**varbinary**
  
## <a name="remarks"></a>解説  
**CERTENCODED**と**CERTPRIVATEKEY**一緒に使用するバイナリ形式で証明書の異なる部分を返します。
  
## <a name="permissions"></a>Permissions  
**CERTPRIVATEKEY**はパブリックに使用できます。
  
## <a name="examples"></a>使用例  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20141031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
使用するより複雑な例について**CERTPRIVATEKEY**と**CERTENCODED**証明書を別のデータベースにコピーするには、例 B のトピックを参照してください。 [CERTENCODED (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/certencoded-transact-sql.md).
  
## <a name="see-also"></a>参照
[セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[証明書 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-certificate-transact-sql.md) 
[セキュリティ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/security-functions-transact-sql.md) 
 [sys.certificates & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  

