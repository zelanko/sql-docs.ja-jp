---
title: sp_vupgrade_mergeobjects (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1341450581e420e87a4f68e35613587afb9d3ac9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722986"
---
# <a name="sp_vupgrade_mergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  マージレプリケーションのデータ変更の追跡と適用に使用されるアーティクル固有のトリガー、ストアドプロシージャ、およびビューを再生成します。 このプロシージャは、次のような場合に実行します。  
  
-   レプリケーションによって要求されたオブジェクトが誤って削除された場合。  
  
-   1 つ以上のレプリケーション オブジェクトに修正プログラムなどの更新プログラムを適用する場合で、プログラムに修正が必要な場合。 更新プログラムを適用した後、各ノードでプロシージャを実行します。  
  
 このストアドプロシージャを実行しても、サブスクリプションを再初期化する必要はありません。 Service Pack をインストールする場合、または新しいバージョンのにアップグレードする場合は、この手順は必要ありません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>引数  
`[ @login = ] 'login'`ディストリビューションデータベースに新しいシステムオブジェクトを作成するときに使用するシステム管理者のログインを示します。 *login* のデータ型は **sysname** で、既定値は NULL です。 *Security_mode*が Windows 認証である**1**に設定されている場合、このパラメーターは必要ありません。  
  
`[ @password = ] 'password'`ディストリビューションデータベースに新しいシステムオブジェクトを作成するときに使用するシステム管理者のパスワードを入力します。 *パスワード*は**sysname**,、既定値は **' '** (空の文字列)。 *Security_mode*が Windows 認証である**1**に設定されている場合、このパラメーターは必要ありません。  
  
`[ @security_mode = ] 'security_mode'`ディストリビューションデータベースに新しいシステムオブジェクトを作成するときに使用するログインセキュリティモードを示します。 *security_mode*の部分は**bit**で、既定値は**1**です。 **0**の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が使用されます。 **1**の場合、Windows 認証が使用されます。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_vupgrade_mergeobjects**は、マージレプリケーションでのみ使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [レプリケートされたデータベースのアップグレード](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
