---
title: sp_repladdcolumn (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9cf625ec15b26743f956ee94ce39c9facbd7b803
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされた既存のテーブル アーティクルに列を追加します。 このテーブルをパブリッシュするすべてのパブリッシャーに新しい列を追加することも、テーブルをパブリッシュする特定のパブリケーションに列を追加することもできます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  このストアド プロシージャは、旧バージョンとの互換性のためにサポートされており、非推奨とされます。 のみ使用する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]パブリッシャーと[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーを再パブリッシュします。 この手順で導入されたデータ型の列では使用できません[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引数  
 [ @source_object =] '*source_object*'  
 追加する新しい列が含まれるテーブル アーティクルの名前を指定します。 *source_object*は**nvarchar (358**)、既定値はありません。  
  
 [ @column =] '*列*'  
 レプリケーション用に追加するテーブルの列の名前を指定します。 *列*は**sysname**、既定値はありません。  
  
 [ @typetext =] '*typetext*'  
 追加する列の定義を指定します。 *typetext*は**nvarchar (3000)**、既定値はありません。 たとえば、列 order_filled が追加、および 1 つの文字のフィールド、NULL でないと、既定の値を持つは**N**、order_filled がなります、*列*の定義の中に、パラメーター、列、 **char (1) は NOT NULL CONSTRAINT constraint_name DEFAULT 'n'** なります、 *typetext*パラメーターの値。  
  
 [ @publication_to_add =] '*publication_to_add*'  
 新しい列の追加先となるパブリケーションの名前を指定します。 *publication_to_add*は**nvarchar (4000)**、既定値は**すべて**です。 場合**すべて**、このテーブルを含むすべてのパブリケーションが影響を受けます。 場合*publication_to_add*が指定されている、このパブリケーションのみがある、新しい列を追加します。  
  
 [ @from_agent =] *from_agent*  
 ストアド プロシージャがレプリケーション エージェントにより実行されているかどうかを示します。 *from_agent*は**int**、既定値は**0**値が、 **1**はレプリケーション エージェントによってこのストアド プロシージャが実行されている場合に使用すべてその他の場合、既定値の**0**使用する必要があります。  
  
 [ @schema_change_script =] '*schema_change_script*'  
 パスと名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システムを変更するためのスクリプトは、カスタム ストアド プロシージャを生成します。 *schema_change_script*は**nvarchar (4000)**、既定値は NULL です。 レプリケーションを行うと、トランザクション レプリケーションで使用される 1 つ以上の既定のプロシージャを、ユーザー定義カスタム ストアド プロシージャに置き換えることができます。 *schema_change_script*スキーマの変更がレプリケートされたテーブル アーティクルに sp_repladdcolumn でが行われ、次のいずれかの操作に使用できる後に実行します。  
  
-   カスタム ストアド プロシージャが自動的に再生成される場合*schema_change_script*のためこれらのカスタム ストアド プロシージャを削除し、ユーザー定義カスタム ストアド プロシージャを新しいスキーマをサポートするのに置き換えることができます。  
  
-   カスタム ストアド プロシージャは自動的に再生成されない場合*schema_change_script*をこれらのストアド プロシージャを再生成するために使用するか、ユーザー定義のカスタムを作成するストアド プロシージャです。  
  
 [ @force_invalidate_snapshot =]*更によって*  
 スナップショットを無効にする機能を有効または無効にします。 *更によって*は、**ビット**、既定値は**1**です。  
  
 **1** 、アーティクルへの変更は、スナップショットが無効であることで発生する可能性がありますを指定し、この場合の値であるかどうか**1**新しいスナップショットを作成する権限が与えられます。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。  
  
 [ @force_reinit_subscription =]*更によって*  
 サブスクリプションを再初期化する機能を有効または無効にします。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更によってが再初期化するサブスクリプションを指定します。  
  
 **1**設定すると、アーティクルへの変更が、サブスクリプションを初期化するには、場合、値であるかどうかと**1**サブスクリプションを再初期化が発生するを許可します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 sp_repladdcolumn を実行できるのは、sysadmin 固定サーバー ロールまたは db_owner 固定データベース ロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [SQL Server レプリケーションの非推奨機能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
