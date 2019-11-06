---
title: sp_pdw_add_network_credentials (SQL データ ウェアハウス) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0729eeff-ac7e-43f0-80fa-ff5346a75985
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: da1ba0db4467526ef2b54650020a899f88788648
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008958"
---
# <a name="sppdwaddnetworkcredentials-sql-data-warehouse"></a>sp_pdw_add_network_credentials (SQL データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  ネットワーク資格情報を保存[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]し、サーバーに関連付けます。 たとえば、このストアド プロシージャを使用するため[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または TDE に使用される証明書のバックアップを作成するには、データベースのバックアップを実行し、復元操作は、ターゲット サーバーでの読み取り/書き込みアクセス許可を適切な。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_add_network_credentials 'target_server_name',  'user_name', ꞌpasswordꞌ  
```  
  
## <a name="arguments"></a>引数  
 '*target_server_name*'  
 ターゲット サーバーのホスト名または IP アドレスを指定します。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] このストアド プロシージャに渡されるユーザー名とパスワードの資格情報を使用してこのサーバーがアクセスします。  
  
 InfiniBand ネットワーク経由で接続するには、ターゲット サーバーの InfiniBand IP アドレスを使用します。  
  
 *target_server_name* nvarchar (337) として定義されます。  
  
 '*user_name*'  
 ターゲット サーバーにアクセスする権限を持っているユーザー名を指定します。 ターゲット サーバーの資格情報が既に存在する場合は、新しい資格情報に更新されます。  
  
 *user_name* nvarchar (513) として定義されます。  
  
 '*パスワード*ꞌ  
 パスワードを示す*user_name*します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 必要があります**ALTER SERVER STATE**権限。  
  
## <a name="error-handling"></a>エラー処理  
 [管理] ノードとすべての計算ノードには資格情報の追加が成功しなかった場合、エラーが発生します。  
  
## <a name="general-remarks"></a>全般的な解説  
 このストアド プロシージャの NetworkService アカウントにネットワーク資格情報を追加する[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。 SMP の各インスタンスを実行する、NetworkService アカウント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コントロールのノードと計算ノードにします。 たとえば、バックアップ操作を実行すると、制御ノードおよび各計算ノードは NetworkService アカウントの資格情報を使用してターゲット サーバーへの読み取り、書き込み許可を取得します。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-add-credentials-for-performing-a-database-backup"></a>A. データベースのバックアップを実行するための資格情報を追加します。  
 次の例では、10.172.63.255 の IP アドレスが設定されているターゲット サーバーをドメイン ユーザーの seattle\david のユーザー名とパスワード資格情報を関連付けます。 ユーザー seattle\david は、ターゲット サーバーへの読み取り/書き込み権限を持っています。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] これらの資格情報を格納し、読み取りおよびとバックアップの必要に応じて、ターゲット サーバーの間を書き込み、および復元操作に使用します。  
  
```  
EXEC sp_pdw_add_network_credentials '10.172.63.255', 'seattle\david', '********';  
```  
  
 バックアップ コマンドでは、IP アドレスとして、サーバー名を入力することが必要です。  
  
> [!NOTE]  
>  InfiniBand 経由のデータベースのバックアップを実行するには、サーバーのバックアップの InfiniBand IP アドレスを使用することを確認します。  
  
## <a name="see-also"></a>参照  
 [sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
  

