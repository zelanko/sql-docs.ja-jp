---
title: ENCRYPTBYCERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- ENCRYPTBYCERT
- ENCRYPTBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], encryption
- encryption [SQL Server], certificates
- ENCRYPTBYCERT function
ms.assetid: ab66441f-e2d2-4e3a-bcae-bcc09e12f3c1
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de2ea71c965490320d0f238116270526a240179e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="encryptbycert-transact-sql"></a>ENCRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  証明書の公開キーを使ってデータを暗号化します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EncryptByCert ( certificate_ID , { 'cleartext' | @cleartext } )  
```  
  
## <a name="arguments"></a>引数  
 *certificate_ID*  
 データベース内の証明書の ID。 **int** です。  
  
 *cleartext*  
 証明書で暗号化するデータの文字列を指定します。  
  
 **@cleartext**  
 証明書の公開キーを使用して暗号化されるデータを含む  **nvarchar**、**char**、**varchar**、**binary**、**varbinary**、または**nchar** 型の変数。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>Remarks  
 この関数では、証明書の公開キーを使ってデータを暗号化します。 この暗号文は、対応する秘密キーでのみ暗号化を解除できます。 このような非対称変換は、対称キーを使用する暗号化および暗号化解除と比較して、非常にコストがかかります。 したがって、非対称暗号化は、テーブル内のユーザー データなど、大きなデータセットを処理する場合は推奨されません。  
  
## <a name="examples"></a>使用例  
 次の例では、`@cleartext` という証明書を使用して、`JanainaCert02` に格納されているプレーン テキストを暗号化します。 暗号化されたデータは、テーブル `ProtectedData04` に挿入されます。  
  
```  
INSERT INTO [AdventureWorks2012].[ProtectedData04]   
    VALUES ( N'Data encrypted by certificate ''Shipping04''',  
    EncryptByCert(Cert_ID('JanainaCert02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DECRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
