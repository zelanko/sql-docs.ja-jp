---
title: "ORIGINAL_DB_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ORIGINAL_DB_NAME
- ORIGINAL_DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ORIGINAL_DB_NAME function
ms.assetid: 7dadc40a-1287-4f31-8487-434ee477144d
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b14df393efb9fb2ab6543e66eba763f50b1f00ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="originaldbname-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーがデータベース接続文字列で指定したデータベース名を返します。 これは、データベースを使用して指定されている、 **sqlcmd d**オプション (使用*データベース*) または ODBC データ ソース式 (初期カタログ =*databasename*)。  
  
 このデータベースは、既定のユーザー データベースとは異なります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ORIGINAL_DB_NAME ()  
```  
  
## <a name="remarks"></a>解説  
 初期データベースが指定されていない場合、この関数は空文字列を返します。  
  
## <a name="see-also"></a>参照  
 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)   
 [osql ユーティリティ](../../tools/osql-utility.md)   
 [SQL Server Native Client (&) #40";"ODBC"&"#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  

