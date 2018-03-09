---
title: "sp_vupgrade_mergeobjects (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_vupgrade_mergeobjects
- sp_vupgrade_mergeobjects_TSQL
helpviewer_keywords:
- sp_vupgrade_mergeobjects
ms.assetid: 73257c2e-cc4c-48e7-9d66-7ef045bdd4f5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83c761ec8e22321e1d46a3b9aacaf5c619c45599
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spvupgrademergeobjects-transact-sql"></a>sp_vupgrade_mergeobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ レプリケーションのデータ変更を追跡および適用するために使用される、アーティクル固有のトリガー、ストアド プロシージャ、ビューを再生成します。 このプロシージャは、次の状況で実行します。  
  
-   レプリケーションによって要求されたオブジェクトが誤って削除された場合。  
  
-   1 つ以上のレプリケーション オブジェクトに修正プログラムなどの更新プログラムを適用する場合で、プログラムに修正が必要な場合。 更新プログラムを適用した後、各ノードでプロシージャを実行します。  
  
 このストアド プロシージャを実行するために、サブスクリプションの再初期化は必要ありません。 この手順は、service pack をインストールまたはの新しいバージョンにアップグレードする場合は必要ありません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_vupgrade_mergeobjects [ [@login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @security_mode = ] security_mode ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@login=**] **'***ログイン***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用する、システム管理者のログインを指定します。 *ログイン*は**sysname**、既定値は NULL です。 このパラメーターは不要な場合は*security_mode*に設定されている**1**、つまり Windows 認証です。  
  
 [  **@password=**] **'***パスワード***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用する、システム管理者のパスワードを指定します。 *パスワード*は**sysname**、既定値は**'** (空の文字列)。 このパラメーターは不要な場合は*security_mode*に設定されている**1**、つまり Windows 認証です。  
  
 [  **@security_mode=**] **'***security_mode***'**  
 ディストリビューション データベースに新しいシステム オブジェクトを作成するときに使用する、ログイン セキュリティ モードを指定します。 *security_mode*は**ビット**で、既定値は**1**です。 場合**0**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証が使用されます。 場合**1**、Windows 認証が使用されます。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_vupgrade_mergeobjects**はマージ レプリケーションに対してのみ使用します。  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [レプリケートされたデータベースのアップグレード](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
