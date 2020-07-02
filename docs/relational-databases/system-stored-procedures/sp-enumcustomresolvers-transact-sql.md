---
title: sp_enumcustomresolvers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumcustomresolvers
- sp_enumcustomresolvers_TSQL
helpviewer_keywords:
- sp_enumcustomresolvers
ms.assetid: 81bd0d3a-48dc-42b1-b662-c630f61fc630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 703a301047f029dbd0ba1d67f55aa0e3ce01ff55
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731690"
---
# <a name="sp_enumcustomresolvers-transact-sql"></a>sp_enumcustomresolvers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  使用可能なすべてのビジネスロジックハンドラーと、ディストリビューターに登録されているカスタム競合回避モジュールの一覧を返します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enumcustomresolvers [ [ @distributor =] 'distributor']  
```  
  
## <a name="arguments"></a>引数  
`[ @distributor = ] 'distributor'`カスタム競合回避モジュールが配置されているディストリビューターの名前を指定します。 *ディストリビューター*は**sysname**,、既定値は NULL です。 *このパラメーターは非推奨とされ、将来のリリースで削除されます。*  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**article_resolver**|**nvarchar(255)**|ビジネスロジックハンドラーまたは競合回避モジュールのフレンドリ名。|  
|**resolver_clsid**|**nvarchar (50)**|COM ベースの競合回避モジュールのクラス ID (CLSID) です。 ビジネスロジックハンドラーの場合、この列には0の CLSID 値が返されます。|  
|**is_dotnet_assembly**|**bit**|ビジネス ロジック ハンドラーに対する登録かどうかを示します。<br /><br /> **0** = COM ベースの競合回避モジュール<br /><br /> **1** = ビジネスロジックハンドラー|  
|**dotnet_assembly_name**|**nvarchar(255)**|ビジネス ロジック ハンドラーを実装している [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework アセンブリの名前です。|  
|**dotnet_class_name**|**nvarchar(255)**|は、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> ビジネスロジックハンドラーを実装するためにをオーバーライドするクラスの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_enumcustomresolvers**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_enumcustomresolvers**を実行できるのは、 **sysadmin**固定サーバーロールおよび**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [マージアーティクルのビジネスロジックハンドラーの実装](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [マージアーティクルのカスタム競合回避モジュールの実装](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
