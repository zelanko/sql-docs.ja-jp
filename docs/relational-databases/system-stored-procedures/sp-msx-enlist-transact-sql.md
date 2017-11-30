---
title: "sp_msx_enlist (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_enlist_TSQL
- sp_msx_enlist
dev_langs: TSQL
helpviewer_keywords: sp_msx_enlist
ms.assetid: ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3cfa391a6fd5874b1b9c9edc99d14904e76874cd
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spmsxenlist-transact-sql"></a>sp_msx_enlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マスター サーバー上にある、使用可能なサーバーの一覧に、現在のサーバーを追加します。  
  
> [!CAUTION]  
>  **Sp_msx_enlist**ストアド プロシージャは、レジストリを編集します。 レジストリは手動で編集しないでください。不適切または不正確な変更を加えると、システム構成に重大な問題が生じる場合があります。 熟練したユーザーのみがレジストリ エディターを使用してレジストリを編集することをお勧めします。 詳細については、Microsoft Windows のドキュメントを参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_msx_enlist [@msx_server_name =] 'msx_server'   
     [, [@location =] 'location']  
```  
  
## <a name="arguments"></a>引数  
 [  **@msx_server_name =**] **'***msx_server***'**  
 マルチサーバー管理 (マスター) サーバーの名前です。 *msx_server*は**sysname**、既定値はありません。  
  
 [  **@location =**] **'***場所***'**  
 追加する対象サーバーの場所です。 *場所*は**nvarchar (100)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>Permissions  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のサーバーを `AdventureWorks1` マスター サーバーに追加します。 現在のサーバーの場所は、`Building 21, Room 309, Rack 5`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_msx_defect &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [xp_cmdshell &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)  
  
  
