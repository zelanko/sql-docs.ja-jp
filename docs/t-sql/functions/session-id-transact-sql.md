---
title: "SESSION_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2a0d500a-f6c8-490f-9abd-3ae824986404
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9089c21109d6eedb1cdae0082e1530e8d77d9dde
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sessionid-transact-sql"></a>SESSION_ID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  現在の ID を返します[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)]セッションです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 **nvarchar (32)**値。  
  
## <a name="general-remarks"></a>全般的な解説  
 セッション ID は、接続が行われたときに、各ユーザー接続に割り当てられます。 これは、接続の間の永続化します。 接続の終了時に、セッション ID は解放されます。  
  
 セッション ID は、アルファベット文字 'SID' を開始します。 これらは、大文字とセッションの ID を使用するとき大文字で入力する必要があります[!INCLUDE[DWsql](../../includes/dwsql-md.md)]コマンド。  
  
 ビューをクエリする[sys.dm_pdw_exec_sessions](http://msdn.microsoft.com/en-us/5b656c55-427f-4306-8bd9-9d7987c203d9)をこの関数と同じ情報を取得します。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のセッション ID を返します。  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>参照  
 [DB_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/db-name-transact-sql.md)   
 [バージョンと #40 です。SQL Data Warehouse &#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  

