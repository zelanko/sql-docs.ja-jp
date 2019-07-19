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
ms.openlocfilehash: 1b01a48e15c06f021b41b3bded35a0cd2739313c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006917"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされた既存のテーブル アーティクルに列を追加します。 このテーブルをパブリッシュするすべてのパブリッシャーに新しい列を追加することも、テーブルをパブリッシュする特定のパブリケーションに列を追加することもできます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]
>  このストアド プロシージャは非推奨し、旧バージョンとの互換性のためサポートされています。 のみ使用する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]パブリッシャーと[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]再パブリッシュ サブスクライバー。 導入されたデータ型列に対してこのプロシージャを使用する必要があります[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降。  
  
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
 追加する新しい列が含まれるテーブル アーティクルの名前です。 *source_object*は**nvarchar (358**)、既定値はありません。  
  
 [ @column =] '*列*'  
 レプリケーション用に追加するテーブル内の列の名前です。 *列*は**sysname**、既定値はありません。  
  
 [ @typetext =] '*typetext*'  
 追加する列の定義を指定します。 *typetext*は**nvarchar (3000)** 、既定値はありません。 たとえば、列 order_filled が追加、および 1 つのフィールドで、NULL 以外の文字との既定値を持つ**N**、order_filled がなります、*列*パラメーターの定義の中に、列、 **char (1) は NOT NULL CONSTRAINT constraint_name DEFAULT 'n'** なります、 *typetext*パラメーターの値。  
  
 [ @publication_to_add =] '*publication_to_add*'  
 新しい列を追加するパブリケーションの名前です。 *publication_to_add*は**nvarchar (4000)** 、既定値は**すべて**します。 場合**すべて**、このテーブルを含むすべてのパブリケーションが影響を受けます。 場合*publication_to_add*このパブリケーションのみが追加された新しい列を指定します。  
  
 [ @from_agent =] *from_agent*  
 場合は、ストアド プロシージャがレプリケーション エージェントで実行されています。 *from_agent*は**int**、既定値は**0**の値が、 **1**は、レプリケーション エージェントによってこのストアド プロシージャが実行されている場合に使用ごとその他の場合、既定値**0**使用する必要があります。  
  
 [ @schema_change_script =] '*schema_change_script*'  
 パスと名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]生成カスタム ストアド プロシージャを使用して、システムを変更するスクリプト。 *schema_change_script*は**nvarchar (4000)** 、既定値は NULL です。 レプリケーションは、ユーザー定義カスタム ストアド プロシージャに置き換える 1 つ以上のトランザクション レプリケーションで使用される既定のプロシージャを使用できます。 *schema_change_script*スキーマ変更がレプリケートされたテーブル アーティクルに sp_repladdcolumn で行われ、次のいずれかの操作に使用できる後に実行されます。  
  
-   カスタム ストアド プロシージャが自動的に再生成される場合*schema_change_script*にこれらのカスタム ストアド プロシージャを削除し、ユーザー定義カスタム ストアド プロシージャ、新しいスキーマをサポートするで置き換えることができます。  
  
-   カスタム ストアド プロシージャは自動的に再生成されない場合*schema_change_script*をこれらのストアド プロシージャを再生成するために使用するか、ストアド プロシージャをユーザー定義のカスタムを作成します。  
  
 [ @force_invalidate_snapshot =]*更によって*  
 有効またはスナップショットを無効にする機能を無効にします。 *更によって*は、**ビット**、既定値は**1**します。  
  
 **1** 、アーティクルへの変更は、スナップショットが無効であることで発生する可能性がありますを指定します。 場合、値がある場合と**1** 、新しいスナップショットを作成する権限が与えられます。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。  
  
 [ @force_reinit_subscription =]*更によって*  
 有効またはサブスクリプションを再初期化する機能を無効にします。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更では、サブスクリプションを再初期化するのには発生しないことを指定します。  
  
 **1** 、アーティクルへの変更は、再初期化されるサブスクリプションで発生する可能性がありますを指定します。 場合、値がある場合と**1**のサブスクリプションの再初期化を許可します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 sp_repladdcolumn を実行できるのは、sysadmin 固定サーバー ロールまたは db_owner 固定データベース ロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server レプリケーションの非推奨の機能](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
