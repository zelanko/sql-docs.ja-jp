---
title: sp_addserver (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 616b835b2b190346df4891caa4d7295c8fb328e1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022429"
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のローカル インスタンスの名前を定義します。 ときにホストするコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、この名前を変更すると、 **sp_addserver**のインスタンスに通知する、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の新しいコンピューター名。 このプロシージャは、コンピューターでホストされている、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のすべてのインスタンスで実行する必要があります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスの名前は変更できません。 名前付きインスタンスのインスタンス名を変更するには、指定した名前で新しいインスタンスをインストールし、古いインスタンスからデータベース ファイルをデタッチし、新しいインスタンスにデータベースをアタッチして古いインスタンスをドロップします。 または、クライアント コンピューター上でクライアント別名を作成して、サーバー コンピューター上のインスタンス名を変更せずに、接続を別のサーバーとインスタンス名か **サーバー:ポート** の組み合せにリダイレクトできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @server = ] 'server'` サーバーの名前です。 サーバー名は一意で、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコンピューター名の規則に従っている必要があります。ただし、スペースは使用できません。 *server* のデータ型は **sysname**で、既定値はありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンスがコンピューターにインストールされている場合、インスタンスは別のサーバー上にあるように動作します。 参照することで、名前付きインスタンスを指定*server*として*servername \instancename*します。  
  
`[ @local = ] 'LOCAL'` 指定するローカル サーバーとして追加されているサーバー。 **@local** **varchar (10)** 、既定値は NULL です。 指定する **@local** として**ローカル**定義 **@server** 原因として、ローカル サーバーの名前として、@@SERVERNAME値を返す関数 *server* します。  
  
 インストール中、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによってこの変数がコンピューター名に設定されます。 既定では、追加構成を行うことなく、ユーザーはこのコンピューター名を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続できます。  
  
 ローカル定義は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] を再起動した後に有効になります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の各インスタンスでは、1 つのローカル サーバーだけを定義できます。  
  
`[ @duplicate_ok = ] 'duplicate_OK'` 重複するサーバー名が許可されているかどうかを指定します。 **@duplicate_OK** **varchar (13)** 、既定値は NULL です。 **@duplicate_OK** 値を持つことができますのみ**duplicate_OK**または NULL。 場合**duplicate_OK**を指定し、既に追加されているサーバー名が存在する、エラーは発生しません。 名前付きパラメーターを使用しない場合 **@local** 指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 を設定または サーバー オプションをオフにするには使用**sp_serveroption**します。  
  
 **sp_addserver**ユーザー定義のトランザクション内で使用することはできません。  
  
 使用して**sp_addserver**リモート サーバーを廃止を追加します。 代わりに [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) を使用してください。  
  
## <a name="permissions"></a>アクセス許可  
 **setupadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] をホストしているコンピューターの名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エントリを `ACCOUNTS`に変更します。  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>関連項目  
 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更します。](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
