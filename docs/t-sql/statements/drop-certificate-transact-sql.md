---
title: DROP CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP CERTIFICATE
- DROP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], removing
- removing certificates
- dropping certificates
- DROP CERTIFICATE statement
- deleting certificates
ms.assetid: 5704aa04-68a3-4b29-b62b-8868af487817
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 26419d80149f0bc2fcb78a113a6f9c90ea090c05
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="drop-certificate-transact-sql"></a>DROP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースから証明書を削除します。  
  
> [!IMPORTANT]  
>  データベースの暗号化に使用されていた証明書のバックアップは、データベースで暗号化を無効にした後も保持しておく必要があります。 データベースが暗号化されなくなっても、トランザクション ログの一部はまだ保護されたままの場合があるため、データベースの完全バックアップが実行されるまでは、一部の操作で証明書が必要になることがあります。 証明書は、データベースが暗号化されていたときに作成されたバックアップから復元する場合にも必要です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP CERTIFICATE certificate_name  
```  
  
## <a name="arguments"></a>引数  
 *certificate_name*  
 データベースに認識される証明書の一意な名前を指定します。  
  
## <a name="remarks"></a>Remarks  
 エンティティが関連付けられていない場合にのみ、証明書は削除できます。  
  
## <a name="permissions"></a>アクセス許可  
 証明書に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、証明書 `Shipping04` をデータベース `AdventureWorks` から削除します。  
  
```  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、証明書 `Shipping04` を削除します。  
  
```  
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="see-also"></a>参照  
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

