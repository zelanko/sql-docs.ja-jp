---
title: sp_register_custom_scripting (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c2220495d256e1f38aecd5cd64c8d43a88c8f25f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spregistercustomscripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーションを行うと、トランザクション レプリケーションで使用される 1 つ以上の既定のプロシージャを、ユーザー定義カスタム ストアド プロシージャに置き換えることができます。 レプリケートされたテーブルにスキーマ変更が行われると、これらのストアド プロシージャは再作成されます。 **sp_register_custom_scripting**ストアド プロシージャを登録または[!INCLUDE[tsql](../../includes/tsql-md.md)]新しいユーザー定義カスタム ストアド プロシージャに対する定義のスクリプトにスキーマ変更が発生したときに実行されるスクリプト ファイル。 この新しいユーザー定義カスタム ストアド プロシージャには、テーブルに対する新しいスキーマを反映する必要があります。 **sp_register_custom_scripting**はパブリッシャーのパブリケーション データベースで実行し、スキーマ変更が発生したときに、サブスクライバー側で実行が登録されているスクリプト ファイルまたはストアド プロシージャです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@type** =] **'***型***'**  
 登録するカスタム ストアド プロシージャまたはスクリプトの種類を指定します。 *型*は**varchar (16)**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|**insert**|登録したカスタム ストアド プロシージャを、INSERT ステートメントがレプリケートされるときに実行。|  
|**更新プログラム**|登録したカスタム ストアド プロシージャを、UPDATE ステートメントがレプリケートされるときに実行。|  
|**delete**|登録したカスタム ストアド プロシージャを、DELETE ステートメントがレプリケートされるときに実行。|  
|**custom_script**|スクリプトをデータ定義言語 (DDL) トリガーの最後に実行。|  
  
 [ **@value**=] **'***値***'**  
 登録するストアド プロシージャの名前または登録する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルの名前とその完全修飾パスを指定します。 *値*は**nvarchar (1024)**、既定値はありません。  
  
> [!NOTE]  
>  NULL を指定する*値*パラメーターには、実行中の場合と同じ、以前に登録されたスクリプトが登録解除[sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)です。  
  
 ときの値*型*は**custom_script**の完全なパスと名前、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプト ファイルが必要です。 それ以外の場合、*値*登録済みのストアド プロシージャの名前を指定する必要があります。  
  
 [ **@publication**=] **'***パブリケーション***'**  
 カスタム ストアド プロシージャまたはスクリプトを登録するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は**NULL**です。  
  
 [ **@article**=] **'***記事***'**  
 カスタム ストアド プロシージャまたはスクリプトを登録するアーティクルの名前を指定します。 *記事*は**sysname**、既定値は**NULL**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_register_custom_scripting**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 このストアド プロシージャは、レプリケートされるテーブルにスキーマ変更を行う前に実行する必要があります。 詳細については、このストアド プロシージャを使用して、次を参照してください。[を再生成カスタム トランザクション プロシージャ スキーマ変更の反映](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md)です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、または**db_ddladmin**固定データベース ロールが実行できる**sp _register_custom_scripting**です。  
  
## <a name="see-also"></a>参照  
 [sp_unregister_custom_scripting &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
