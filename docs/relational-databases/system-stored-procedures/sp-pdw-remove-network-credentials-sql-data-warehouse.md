---
title: sp_pdw_remove_network_credentials (SQL データ ウェアハウス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.subservice: design
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d3c19439a481b843edec8210f83a4a82e5dd27a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056439"
---
# <a name="sppdwremovenetworkcredentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials (SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  これにより、ネットワークの資格情報に格納されている [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ネットワーク ファイル共有にアクセスします。 たとえば、このストアド プロシージャを使用して権限を削除する [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] バックアップと復元操作は、自社のネットワーク内に存在するサーバーで実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>引数  
 '*target_server_name*'  
 ターゲット サーバーのホスト名または IP アドレスを指定します。 このサーバーへのアクセスに資格情報が削除される予定 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 これは、チームで管理されている実際のターゲット サーバーでどのアクセス許可も変更、削除するものではありません。  
  
 *target_server_name* nvarchar (337) として定義されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 必要があります**ALTER SERVER STATE**権限。  
  
## <a name="error-handling"></a>エラー処理  
 [管理] ノードとすべての計算ノードには資格情報の削除が成功しなかった場合、エラーが発生します。  
  
## <a name="general-remarks"></a>全般的な解説  
 このストアド プロシージャでは、ネットワーク資格情報を削除の NetworkService アカウントから [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 SMP の各インスタンスを実行する、NetworkService アカウント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コントロールのノードと計算ノードにします。 たとえば、バックアップ操作を実行すると、制御ノードおよび各計算ノードは NetworkService アカウントの資格情報を使用してターゲット サーバーにアクセスします。  
  
## <a name="metadata"></a>メタデータ  
 すべての資格情報を一覧表示し、資格情報が削除されていることを確認するには、使用[sys.dm_pdw_network_credentials &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)します。  
  
 資格情報を追加する[sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)します。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>A. データベースのバックアップを実行するための資格情報を削除します。  
 次の例では、ユーザー名とパスワードを 10.192.147.63 の IP アドレスを持つターゲット サーバーにアクセスするための資格情報を削除します。  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

