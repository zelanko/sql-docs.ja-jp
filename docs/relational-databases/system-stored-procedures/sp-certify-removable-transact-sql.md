---
title: "sp_certify_removable (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs: TSQL
helpviewer_keywords: sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab84edebdbc4a8775e9ce4a50e3236b1377b3932
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spcertifyremovable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リムーバブル メディア上でデータベースが配布用に正しく構成されているかどうか確認し、問題があればユーザーにレポートします。  
  
> **重要!!** [!含める[ssNoteDepFutureAvoid](../../t-sql/statements/create-database-sql-server-transact-sql.md)代わりにします。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@dbname=**] **'***dbname***'**  
 確認するデータベースを指定します。 *dbname*は**sysname**です。  
  
 [  **@autofix=**] **'auto'**  
 データベースとすべてのデータベース オブジェクトの所有権をシステム管理者に与え、ユーザー作成のデータベース ユーザーと既定値以外の権限を削除します。 *自動*は**nvarchar (4)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 データベースが正しく構成されている場合**sp_certify_removable**は、次を実行します。  
  
-   データベースをオフラインに設定し、ファイルをコピーできるようにする。  
  
-   すべてのテーブルに関する統計を更新し、所有権やユーザーに関する問題をレポートする。  
  
-   データ ファイル グループを読み取り専用としてマークし、ファイルを読み取り専用メディアにコピーできるようにする。  
  
 システム管理者は、データベースとすべてのデータベース オブジェクトの所有者であることが必要です。 システム管理者が実行されているすべてのサーバー上に存在する既知のユーザー [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースが後で配布され、インストールされているときに存在するが予想されます。  
  
 実行する場合**sp_certify_removable**せず、**自動**値とは、次の条件のいずれかに関する情報を返します。  
  
-   システム管理者がデータベース所有者ではない。  
  
-   ユーザーが作成したユーザーが存在する。  
  
-   システム管理者がデータベースのすべてのオブジェクトを所有していない。  
  
-   既定値以外の権限が与えられている。  
  
 これらの問題は次の方法で解決できます。  
  
-   使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ツールおよびプロシージャを実行し**sp_certify_removable**もう一度です。  
  
-   実行するだけで**sp_certify_removable**で、**自動**値。  
  
 このストアド プロシージャでは、ユーザーとユーザーの権限だけがチェックされます。 データベースにはグループを追加でき、そのグループに権限を与えることができます。 詳細については、「[GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 実行のアクセス許可がのメンバーに限定する、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、`inventory` データベースを削除できるかどうかを確認します。  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
