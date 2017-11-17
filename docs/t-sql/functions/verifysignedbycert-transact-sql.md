---
title: "VERIFYSIGNEDBYCERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- VERIFYSIGNEDBYCERT
- VERIFYSIGNEDBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- digitally signed data for changes [SQL Server]
- verifying digitally signed data for changes
- testing digitally signed data for changes
- checking digitally signed data for changes
- VERIFYSIGNEDBYCERT
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 4e041f33-60c4-4190-91c7-220d51dd6c8f
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d4725d6e9e28100333040061eafb54f07db9066
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="verifysignedbycert-transact-sql"></a>VERIFYSIGNEDBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  デジタル署名付きデータが、署名された後に変更されているかどうかをテストします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
VerifySignedByCert( Cert_ID , signed_data , signature )  
```  
  
## <a name="arguments"></a>引数  
 *Cert_ID*  
 データベース内の証明書の ID を指定します。 *Cert_ID*は**int**です。  
  
 *signed_data*  
 型の変数は、 **nvarchar**、 **char**、 **varchar**、または**nchar**証明書で署名されているデータを格納します。  
  
 *署名*  
 署名付きデータにアタッチされた署名を指定します。 *署名*は**varbinary**です。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
 署名付きデータが変更されていない場合は 1、変更されている場合は 0 が返されます。  
  
## <a name="remarks"></a>解説  
 **VerifySignedBycert**指定された証明書の公開キーを使用して、データの署名を復号化し、データの新しく計算された MD5 ハッシュを復号化された値を比較します。 値が一致すると、その署名が有効であることが確認されます。  
  
## <a name="permissions"></a>Permissions  
 証明書に対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-verifying-that-signed-data-has-not-been-tampered-with"></a>A. 署名付きデータが変更されていないことを確認する  
 次の例をテストするかどうかの情報は、`Signed_Data`という証明書で署名された後で変更された`Shipping04`です。 署名は `DataSignature` に格納されています。 証明書、`Shipping04`に渡される`Cert_ID`データベースに証明書の ID が返されます。 場合`VerifySignedByCert`署名が正しいは、1 を返します。 `VerifySignedByCert` で 0 が返された場合、`Signed_Data` 内のデータは、`DataSignature` の生成に使用されたデータではありません。 この場合、いずれか`Signed_Data`が署名された後に変更されたまたは`Signed_Data`別の証明書で署名されました。  
  
```  
SELECT Data, VerifySignedByCert( Cert_Id( 'Shipping04' ),  
    Signed_Data, DataSignature ) AS IsSignatureValid  
FROM [AdventureWorks2012].[SignedData04]   
WHERE Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
### <a name="b-returning-only-records-that-have-a-valid-signature"></a>B. 有効な署名が含まれるレコードのみを返す  
 このクエリは、証明書を使用して署名された後に変更されていないレコードだけを返します`Shipping04`です。  
  
```  
SELECT Data FROM [AdventureWorks2012].[SignedData04]   
WHERE VerifySignedByCert( Cert_Id( 'Shipping04' ), Data,   
    DataSignature ) = 1   
AND Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CERT_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cert-id-transact-sql.md)   
 [SIGNBYCERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/signbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [証明書 &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

