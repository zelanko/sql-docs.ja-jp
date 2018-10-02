---
title: CERTPRIVATEKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPRIVATEKEY
- CERTPRIVATEKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTPRIVATEKEY
ms.assetid: 33e0f01e-39ac-46da-94ff-fe53b1116df4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3d5605a133c4edb9a54b919522d17ffd65478a82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652100"
---
# <a name="certprivatekey-transact-sql"></a>CERTPRIVATEKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

この関数は、証明書の秘密キーをバイナリ形式で返します。 この関数は 3 つの引数を受け取ります。
-   証明書 ID。  
-   関数によって返される秘密キーのビットの暗号化に使用される暗号化パスワード。 この方法では、ユーザーにクリア テキストとしてキーを公開しません。  
-   オプションの暗号化解除パスワード。 証明書の秘密キーを暗号化解除するために指定された暗号化解除パスワードが使用されます。 それ以外の場合、データベース マスター キーが使用されます。  
  
証明書の秘密キーへのアクセス権を持つユーザーだけが、この関数を使用できます。 この関数は、秘密キーを PVK 形式で返します。
  
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
証明書の **certificate_id**。 この値は、sys.certificates または [CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md) 関数から取得します。 *cert_id* は **int** データ型です。
  
*encryption_password*  
返されたバイナリ値の暗号化に使用するパスワード。
  
*decryption_password*  
返されたバイナリ値の暗号化の解除に使用するパスワード。
  
## <a name="return-types"></a>戻り値の型
**varbinary**
  
## <a name="remarks"></a>Remarks  
**CERTENCODED** と **CERTPRIVATEKEY** を一緒に使用すると、バイナリの形式で証明書の異なる部分を返します。
  
## <a name="permissions"></a>アクセス許可  
**CERTPRIVATEKEY** はパブリックに使用できます。
  
## <a name="examples"></a>使用例  
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Use 5tr0ng P^55Words'  
GO  
CREATE CERTIFICATE Shipping04   
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20401031';  
GO  
SELECT CERTPRIVATEKEY(CERT_ID('Shipping04'), 'jklalkaa/; uia3dd');  
```  
  
**CERTPRIVATEKEY** と **CERTENCODED** を使用して証明書を別のデータベースにコピーするより複雑な例については、 [CERTENCODED &#40;Transact-SQL&#41;](../../t-sql/functions/certencoded-transact-sql.md) の例 B を参照してください。
  
## <a name="see-also"></a>参照
[セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)
[セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
