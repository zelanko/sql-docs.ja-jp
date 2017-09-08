---
title: "ドロップ ユーザー (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_USER_TSQL
- DROP USER
dev_langs:
- TSQL
helpviewer_keywords:
- dropping users
- DROP USER statement
- deleting users
- database user removal [SQL Server]
- removing users
- users [SQL Server], removing
ms.assetid: d6e0e21a-7568-4321-b6d6-bcfba183a719
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d1af03b517cbef82d0ed1c9f7affb6b7d6eda21
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-user-transact-sql"></a>DROP USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースからユーザーを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP USER [ IF EXISTS ] user_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP USER user_name  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)、 [!INCLUDE[sssds](../../includes/sssds-md.md)])。  
  
 条件付きでは既に存在する場合にのみ、ユーザーを削除します。  
  
 *user_name*  
 データベース内でユーザーを識別する名前を指定します。  
  
## <a name="remarks"></a>解説  
 セキュリティ保護可能なリソースを所有するユーザーは、データベースから削除できません。 セキュリティ保護可能なリソースを所有するデータベース ユーザーを削除するには、そのリソースの所有権を削除または譲渡する必要があります。  
  
 guest ユーザーは削除できませんが、master または tempdb 以外のデータベースでは、REVOKE CONNECT FROM GUEST を実行して CONNECT 権限を取り消すことにより、guest ユーザーを無効にできます。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER ANY USER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`AbolrousHazem` データベースからデータベース ユーザー `AdventureWorks2012` を削除します。  
  
```  
DROP USER AbolrousHazem;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [ALTER USER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-user-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  

