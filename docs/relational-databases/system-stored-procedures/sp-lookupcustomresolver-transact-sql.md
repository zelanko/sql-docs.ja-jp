---
title: sp_lookupcustomresolver (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad45f26fbd1c6b7f9488497333f5ba44a2b5fa8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ビジネス ロジック ハンドラーの情報、またはディストリビューターで登録されている COM ベースのカスタム競合回避モジュールのクラス ID (CLSID) の値を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@article_resolver =** ] **'***article_resolver***'**  
 登録を解除するカスタム ビジネス ロジックの名前を指定します。 *article_resolver*は**nvarchar (255)**、既定値はありません。 削除されるビジネス ロジックが COM コンポーネントの場合、そのコンポーネントの表示名です。 ビジネス ロジックがある場合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework アセンブリでは、このパラメーターは、アセンブリの名前。  
  
 [ **@resolver_clsid**=] **'***resolver_clsid***'**出力  
 指定されたカスタム ビジネス ロジックの名前に関連付けられている COM オブジェクトの CLSID 値は、 *article_resolver*パラメーター。 *resolver_clsid*は**nvarchar (50)**、既定値は NULL です。  
  
 [  **@is_dotnet_assembly=** ] **'***@is_dotnet_assembly***'**出力  
 登録するカスタム ビジネス ロジックの種類を指定します。 *is_dotnet_assembly*は**ビット**、既定値は 0 です。 **1**登録するカスタム ビジネス ロジックがビジネス ロジック ハンドラー アセンブリであることを示します**0** COM コンポーネントであることを示します。  
  
 [  **@dotnet_assembly_name=** ] **'***@dotnet_assembly_name***'**出力  
 ビジネス ロジック ハンドラーを実装するアセンブリの名前を指定します。 *@dotnet_assembly_name*は**nvarchar (255)**既定値は NULL です。  
  
 [  **@dotnet_class_name=** ] **'***@dotnet_class_name***'**出力  
 オーバーライドするクラスの名前を指定<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule>ビジネス ロジック ハンドラーを実装します。 *@dotnet_class_name*は**nvarchar (255)**既定値は NULL です。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**既定値は NULL です。 このパラメーターは、ストアド プロシージャをパブリッシャーから呼び出さないときに使用します。 指定しない場合、ローカル サーバーがパブリッシャーであると見なされます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_lookupcustomresolver**はマージ レプリケーションで使用します。  
  
 **sp_lookupcustomresolver** 、NULL 値を返します*resolver_clsid*ときに、コンポーネントが登録されていない分布と「00000000-0000-0000-0000-000000000000」の値に、登録が属している場合、.NET framework アセンブリは、ビジネス ロジック ハンドラーとして登録します。  
  
 **sp_lookupcustomresolver**によって呼び出される[sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)と[sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)を指定された検証*article_resolver*です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **db_owner** 、パブリケーション データベースの固定データベース ロールが実行できる**sp_lookupcustomresolver**です。  
  
## <a name="see-also"></a>参照  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [マージ同期中にビジネス ロジックを実行します。](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [マージ アーティクルの競合回避モジュールを指定します。](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
