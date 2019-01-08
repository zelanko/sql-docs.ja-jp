---
title: sp_repladdcolumn (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d50f940b191ee057febb81a59b90d6c842cf821
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53211941"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされた既存のテーブル アーティクルに列を追加します。 このテーブルをパブリッシュするすべてのパブリッシャーに新しい列を追加することも、テーブルをパブリッシュする特定のパブリケーションに列を追加することもできます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]
>  このストアド プロシージャは、旧バージョンとの互換性のためにサポートされており、非推奨とされます。 のみ使用する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]パブリッシャーと[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]再パブリッシュ サブスクライバー。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で導入されたデータ型の列に対してこのプロシージャを使用しないでください。  
  
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
 追加する列の定義を指定します。 *typetext*は**nvarchar (3000)**、既定値はありません。 たとえば、列 order_filled が追加、および 1 つのフィールドで、NULL 以外の文字との既定値を持つ**N**、order_filled がなります、*列*パラメーターの定義の中に、列、 **char (1) は NOT NULL CONSTRAINT constraint_name DEFAULT 'n'** なります、 *typetext*パラメーターの値。  
  
 [ @publication_to_add =] '*publication_to_add*'  
 新しい列の追加先となるパブリケーションの名前を指定します。 *publication_to_add*は**nvarchar (4000)**、既定値は**すべて**します。 場合**すべて**、このテーブルを含むすべてのパブリケーションが影響を受けます。 場合*publication_to_add*このパブリケーションのみが追加された新しい列を指定します。  
  
 [ @from_agent =] *from_agent*  
 ストアド プロシージャがレプリケーション エージェントにより実行されているかどうかを示します。 *from_agent*は**int**、既定値は**0**の値が、 **1**は、レプリケーション エージェントによってこのストアド プロシージャが実行されている場合に使用ごとその他の場合、既定値**0**使用する必要があります。  
  
 [ @schema_change_script =] '*schema_change_script*'  
 システム生成カスタム ストアド プロシージャを修正するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スクリプトの名前とパスを指定します。 *schema_change_script*は**nvarchar (4000)**、既定値は NULL です。 レプリケーションを行うと、トランザクション レプリケーションで使用される 1 つ以上の既定のプロシージャを、ユーザー定義カスタム ストアド プロシージャに置き換えることができます。 *schema_change_script*スキーマ変更がレプリケートされたテーブル アーティクルに sp_repladdcolumn で行われ、次のいずれかの操作に使用できる後に実行されます。  
  
-   カスタム ストアド プロシージャが自動的に再生成される場合*schema_change_script*にこれらのカスタム ストアド プロシージャを削除し、ユーザー定義カスタム ストアド プロシージャ、新しいスキーマをサポートするで置き換えることができます。  
  
-   カスタム ストアド プロシージャは自動的に再生成されない場合*schema_change_script*をこれらのストアド プロシージャを再生成するために使用するか、ストアド プロシージャをユーザー定義のカスタムを作成します。  
  
 [ @force_invalidate_snapshot =]*更によって*  
 スナップショットを無効にする機能を有効または無効にします。 *更によって*は、**ビット**、既定値は**1**します。  
  
 **1** 、アーティクルへの変更は、スナップショットが無効であることで発生する可能性がありますを指定します。 場合、値がある場合と**1** 、新しいスナップショットを作成する権限が与えられます。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。  
  
 [ @force_reinit_subscription =]*更によって*  
 サブスクリプションを再初期化する機能を有効または無効にします。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更では、サブスクリプションを再初期化するのには発生しないことを指定します。  
  
 **1** 、アーティクルへの変更は、再初期化されるサブスクリプションで発生する可能性がありますを指定します。 場合、値がある場合と**1**のサブスクリプションの再初期化を許可します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 sp_repladdcolumn を実行できるのは、sysadmin 固定サーバー ロールまたは db_owner 固定データベース ロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [SQL Server レプリケーションの非推奨の機能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
