---
title: "GRANT システム オブジェクトの権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], system objects
- system objects [SQL Server]
- GRANT statement, system objects
ms.assetid: 9d4e89f4-478f-419a-8b50-b096771e3880
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3bd1f78212ef050c6610eab57f95cd44d51d9fbf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-system-object-permissions-transact-sql"></a>GRANT (システム オブジェクトの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システム ストアド プロシージャ、拡張ストアド プロシージャ、関数、ビューなどのシステム オブジェクトに対する権限を許可します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GRANT { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>引数  
 [sys].  
 sys 修飾子は、カタログ ビューおよび動的カタログ ビューを指定する場合にのみ必要です。  
  
 *system_object*  
 権限が許可されているオブジェクトを指定します。  
  
 *プリンシパル*  
 権限を許可するプリンシパルを指定します。  
  
## <a name="remarks"></a>解説  
 このステートメントを使用すると、特定のストアド プロシージャ、拡張ストアド プロシージャ、テーブル値関数、スカラー関数、ビュー、カタログ ビュー、互換ビュー、INFORMATION_SCHEMA ビュー、動的管理ビュー、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってインストールされたシステム テーブルに対する権限を許可できます。 これらのシステム オブジェクトはそれぞれ、サーバーのリソース データベース (mssqlsystemresource) に一意なレコードとして存在しています。 リソース データベースは読み取り専用です。 オブジェクトへのリンクは、各データベースの sys スキーマでは 1 レコードとして表されます。 システム オブジェクトを実行または選択する権限は、許可、拒否、および取り消しが可能です。  
  
 オブジェクトを実行または選択する権限を許可しても、そのオブジェクトの使用に必要なすべての権限が与えられるわけではありません。 ほとんどのオブジェクトでは、操作の実行に追加の権限が必要です。 たとえば、ユーザーに対して sp_addlinkedserver の EXECUTE 権限が許可されていても、sysadmin 固定サーバー ロールのメンバーでない限り、そのユーザーはリンク サーバーを作成できません。  
  
 既定の名前解決では、修飾子のないプロシージャ名はリソース データベースとして解釈されます。 したがって、sys 修飾子は、カタログ ビューおよび動的カタログ ビューを指定する場合にのみ必要です。  
  
 システム オブジェクトのトリガーおよび列に対する権限の許可はサポートされていません。  
  
 アップグレード中にシステム オブジェクトに対する権限は保持されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 システム オブジェクトは、 [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) カタログ ビューで確認できます。 システム オブジェクトに対する権限は、 [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)カタログ ビュー、master データベースで確認します。  
  
 次のクエリでは、システム オブジェクトの権限に関する情報が返されます。  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-granting-select-permission-on-a-view"></a>A. ビューに対する SELECT 権限を許可する  
 次の例、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`Sylvester1`を一覧表示するビューを選択する権限[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 例では、しでメタデータを表示するために必要な追加のアクセス許可を付与する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーが所有していないログインします。  
  
```  
USE AdventureWorks2012;  
GRANT SELECT ON sys.sql_logins TO Sylvester1;  
GRANT VIEW SERVER STATE to Sylvester1;  
GO  
```  
  
### <a name="b-granting-execute-permission-on-an-extended-stored-procedure"></a>B. 拡張ストアド プロシージャに対する EXECUTE 権限を許可する  
 次の例では、`EXECUTE` に対し、`xp_readmail` の `Sylvester1` 権限を許可します。  
  
```  
GRANT EXECUTE ON xp_readmail TO Sylvester1;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.system_objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  

