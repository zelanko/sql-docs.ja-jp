---
title: sp_repldropcolumn (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_repldropcolumn_TSQL
- sp_repldropcolumn
helpviewer_keywords:
- sp_repldropcolumn
ms.assetid: fdc1ec5f-f108-42b4-a2d8-f06a71913ab8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2613b4c2aded7ee192bdd456b3d9d51ec1587eda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33002355"
---
# <a name="sprepldropcolumn-transact-sql"></a>sp_repldropcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされた既存のテーブル アーティクルから列を削除します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  このストアド プロシージャは、主に旧バージョンとの互換性のためにサポートされており、非推奨とされます。 のみ使用する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]パブリッシャーと[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーを再パブリッシュします。 この手順で導入されたデータ型の列では使用できません[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repldropcolumn [ @source_object = ] 'source_object', [ @column = ] 'column'   
    [ , [ @from_agent = ] from_agent]   
    [ , [ @schema_change_script = ] 'schema_change_script' ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>引数  
 [ @source_object =] '*source_object*'  
 削除する列が含まれるテーブル アーティクルの名前を指定します。 *source_object*は nvarchar (258)、既定値はありません。  
  
 [ @column =] '*列*'  
 テーブル内の削除する列の名前を指定します。 *列*は sysname で、既定値はありません。  
  
 [ @from_agent =] *from_agent*  
 ストアド プロシージャがレプリケーション エージェントにより実行されているかどうかを示します。 *from_agent*は int で、既定値は 0、1 の値を使用してこのストアド プロシージャは、レプリケーション エージェントにより実行されていると、他のすべてのケースで、既定値は 0 を使用する必要があります。  
  
 [ @schema_change_script =] '*schema_change_script*'  
 パスと名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システムを変更するためのスクリプトは、カスタム ストアド プロシージャを生成します。 *schema_change_script*は nvarchar (4000)、既定値は NULL です。 レプリケーションを行うと、トランザクション レプリケーションで使用される 1 つ以上の既定のプロシージャを、ユーザー定義カスタム ストアド プロシージャに置き換えることができます。 *schema_change_script*スキーマの変更は、sp_repldropcolumn でレプリケートされたテーブル アーティクルに行われ、次のいずれかの操作に使用できる後に実行されます。  
  
-   カスタム ストアド プロシージャが自動的に再生成される場合*schema_change_script*のためこれらのカスタム ストアド プロシージャを削除し、ユーザー定義カスタム ストアド プロシージャを新しいスキーマをサポートするのに置き換えることができます。  
  
-   カスタム ストアド プロシージャは自動的に再生成されない場合*schema_change_script*をこれらのストアド プロシージャを再生成するために使用するか、ユーザー定義のカスタムを作成するストアド プロシージャです。  
  
 [ @force_invalidate_snapshot =]*更によって*  
 スナップショットを無効にする機能を有効または無効にします。 *更によって*ビットで、既定値は 1 です。  
  
 1 に設定すると、アーティクルへの変更によってスナップショットが無効になることがあります。この場合、値 1 では新しいスナップショットを作成する権限が与えられます。  
  
 0 に設定すると、アーティクルへの変更によってスナップショットが無効になることはありません。  
  
 [ @force_reinit_subscription =]*更によって*  
 サブスクリプションを再初期化する機能を有効または無効にします。 *更によって*は bit で、既定値は 0 です。  
  
 0 に設定すると、アーティクルへの変更によってサブスクリプションが再初期化されることはありません。  
  
 1 に設定すると、アーティクルへの変更によってサブスクリプションが再初期化されることがあります。この場合、値 1 ではサブスクリプションを再初期化する権限が与えられます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 sp_repldropcolumn を実行できるのは、パブリッシャー側の sysadmin 固定サーバー ロールのメンバー、またはパブリケーション データベースの db_owner 固定データベース ロールや db_ddladmin 固定データベース ロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [SQL Server レプリケーションの非推奨機能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
