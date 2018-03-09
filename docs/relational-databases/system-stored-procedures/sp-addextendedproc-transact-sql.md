---
title: "sp_addextendedproc (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c17007edd948c5d914c6fc2ad602fb4cebb7d13
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  拡張ストアド プロシージャに新しい名前を登録[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに [CLR 統合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>引数  
 [  **@functname =** ] **'***プロシージャ***'**  
 ダイナミックリンク ライブラリ (DLL) の内部で呼び出す関数の名前を指定します。 *プロシージャ*は**nvarchar (517)**、既定値はありません。 *プロシージャ*形式で所有者名を含めることができます必要に応じて*owner.function*です。  
  
 [  **@dllname =** ] **'***dll***'**  
 関数が含まれている DLL の名前を指定します。 *dll*は**varchar (255)**、既定値はありません。 DLL の完全パスを指定することをお勧めします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 拡張ストアド プロシージャを作成した後に追加する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して**sp_addextendedproc**です。 詳細については、次を参照してください。[拡張ストアド プロシージャを SQL Server に追加する](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md)です。  
  
 この手順でのみ実行できる、**マスター**データベース。 以外のデータベースから拡張ストアド プロシージャを実行する**マスター**を使用して拡張ストアド プロシージャの名前を修飾**マスター**です。  
  
 **sp_addextendedproc**にエントリを追加、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビュー、新しい名前を登録する拡張ストアド プロシージャ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 内のエントリも追加、 [sys.extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md)カタログ ビューです。  
  
> [!IMPORTANT]  
>  完全パスで登録されなかった既存の DLL は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレード後、機能しなくなります。 問題を解決するには使用**sp_dropextendedproc** 、DLL の登録を解除してと共に登録し、 **sp_addextendedproc**、完全なパスを指定します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_addextendedproc**です。  
  
## <a name="examples"></a>使用例  
 次の例では追加、 **xp_hello**拡張ストアド プロシージャです。  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>参照  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
