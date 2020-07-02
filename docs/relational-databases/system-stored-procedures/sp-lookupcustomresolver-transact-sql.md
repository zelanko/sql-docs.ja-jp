---
title: sp_lookupcustomresolver (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b86fd5bd04c41d10437a8a0f7bcc21b61ab22fef
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720238"
---
# <a name="sp_lookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  ビジネス ロジック ハンドラーの情報、またはディストリビューターで登録されている COM ベースのカスタム競合回避モジュールのクラス ID (CLSID) の値を返します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
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
`[ @article_resolver = ] 'article_resolver'`登録を解除するカスタムビジネスロジックの名前を指定します。 *article_resolver*は**nvarchar (255)**,、既定値はありません。 削除されるビジネスロジックが COM コンポーネントの場合、このパラメーターはコンポーネントのフレンドリ名です。 ビジネスロジックが [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework アセンブリの場合、このパラメーターはアセンブリの名前です。  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT`*Article_resolver*パラメーターで指定されたカスタムビジネスロジックの名前に関連付けられている COM オブジェクトの CLSID 値を指定します。 *resolver_clsid*は**nvarchar (50)**,、既定値は NULL です。  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT`登録するカスタムビジネスロジックの種類を指定します。 *is_dotnet_assembly*は**ビット**,、既定値は0です。 **1**は、登録されているカスタムビジネスロジックがビジネスロジックハンドラーアセンブリであることを示します。**0**は、COM コンポーネントであることを示します。  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT`は、ビジネスロジックハンドラーを実装するアセンブリの名前です。 *dotnet_assembly_name*は**nvarchar (255)**,、既定値は NULL です。  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT`は、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> ビジネスロジックハンドラーを実装するためにをオーバーライドするクラスの名前です。 *dotnet_class_name*は**nvarchar (255)**,、既定値は NULL です。  
  
`[ @publisher = ] 'publisher'`パブリッシャーの名前を指定します。 *publisher*は**sysname**で、既定値は NULL です。 このパラメーターは、ストアド プロシージャをパブリッシャーから呼び出さないときに使用します。 指定しない場合、ローカル サーバーがパブリッシャーであると見なされます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_lookupcustomresolver**は、マージレプリケーションで使用します。  
  
 **sp_lookupcustomresolver**は、コンポーネントがディストリビューションで登録されていない場合は*resolver_clsid*に NULL 値を返し、登録がビジネスロジックハンドラーとして登録されている .NET Framework アセンブリに属している場合は値 "00000000-0000-0000-0000-000000000000" を返します。  
  
 **sp_lookupcustomresolver**は[sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)によって呼び出され、指定された*article_resolver*を検証する[sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_lookupcustomresolver**を実行できるのは、パブリケーションデータベースの**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [マージレプリケーションの競合検出と解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [マージ同期中のビジネスロジックの実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [マージアーティクルのビジネスロジックハンドラーの実装](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [マージアーティクル競合回避モジュールの指定](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
