---
title: "使用 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/28/2016
ms.prod: sql-non-specified
ms.prod_service: pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USE_TSQL
- USE
dev_langs: TSQL
helpviewer_keywords:
- USE statement
- database context [SQL Server]
- context changes [SQL Server]
- modifying database context
ms.assetid: c05acac8-c063-4770-8e36-d7f71d500b10
caps.latest.revision: "40"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1de8ddd8d109e7ba2b83dd6c940487c6aa3fd155
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="use-transact-sql"></a>USE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  データベース コンテキストを、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の指定したデータベースまたはデータベース スナップショットに変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
USE { database_name }   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 ユーザー コンテキストの切り替え先のデータベースまたはデータベース スナップショットの名前を指定します。 データベースとデータベース スナップショット名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]では、データベース パラメーターは現在のデータベースのみを参照できます。 現在のデータベース以外のデータベースが提供されているかどうか、`USE`ステートメントがないデータベースを切り替える、およびエラー コード 40508 が返されます。 データベースを変更するには、直接データベースに接続する必要があります。 たとえことがあるできますので、USE ステートメントがこのページの上部にある SQL データベースには適用されませんとしてマークされて、`USE`ステートメントのバッチで、何もしません。
  
## <a name="remarks"></a>解説  
 ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続するログイン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが自動的に既定のデータベースに接続されているし、データベース ユーザーのセキュリティ コンテキストを取得します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン用のデータベース ユーザーが 1 人も作成されていない場合、ログインは guest として接続されます。 データベース ユーザーが、データベースに対する CONNECT 権限を持たない場合、USE ステートメントは失敗します。 ログインに既定のデータベースが割り当てられていない場合、既定のデータベースとして master が設定されます。  
  
 USE は、コンパイル時と実行時の両方で実行でき、その効果は直ちに有効になります。 したがって、バッチ内で USE ステートメントの後にあるステートメントは、指定したデータベースで実行されます。  
  
## <a name="permissions"></a>権限  
 切り替え先のデータベースに対する CONNECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース コンテキストを `AdventureWorks2012` データベースに変更します。  
  
```  
USE AdventureWorks2012;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)  
  
  


