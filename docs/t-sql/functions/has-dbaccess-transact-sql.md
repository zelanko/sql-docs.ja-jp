---
title: HAS_DBACCESS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HAS_DBACCESS_TSQL
- HAS_DBACCESS
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- permissions [SQL Server], user access status
- HAS_DBACCESS
- checking permission status
- verifying permission status
- users [SQL Server], access rights status
- testing permissions
- status information [SQL Server], user access
ms.assetid: 99b43a72-0722-4a7b-a493-bdee1c74c7b9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f0463463a489e7a0e2a252aad80fd3e1ce60679
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="hasdbaccess-transact-sql"></a>HAS_DBACCESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  ユーザーが指定のデータベースにアクセスできるかどうかについて情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
HAS_DBACCESS ( 'database_name' )  
```  
  
## <a name="arguments"></a>引数  
 '*database_name*'  
 ユーザーのアクセス情報が必要なデータベースの名前を指定します。 *database_name* は **sysname** です。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 ユーザーがデータベースにアクセスできる場合は 1、アクセスできない場合は 0 が返されます。データベース名が有効でない場合は NULL が返されます。  
  
 データベースがオフラインの場合または異常がある場合は、0 が返されます。  
  
 データベースがシングル ユーザー モードであり、別のユーザーによって使用されている場合も、0 が返されます。  
  
## <a name="permissions"></a>アクセス許可  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のユーザーが `AdventureWorks2012` データベースにアクセスできるかどうかをテストします。  
  
```  
SELECT HAS_DBACCESS('AdventureWorks2012');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、現在のユーザーが `AdventureWorksPDW2012` データベースにアクセスできるかどうかをテストします。  
  
```  
SELECT HAS_DBACCESS('AdventureWorksPDW2012');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [IS_MEMBER &#40;Transact-SQL&#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [IS_SRVROLEMEMBER &#40;Transact-SQL&#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)  
  
  

