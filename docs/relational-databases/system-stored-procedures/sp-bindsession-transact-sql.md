---
title: "sp_bindsession (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_bindsession
- sp_bindsession_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_bindsession
ms.assetid: 1436fe21-ad00-4a98-aca1-1451a5e571d2
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c426c9ecca2c67dd1892d3d09a800fd229291598
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spbindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バインドまたはの同じインスタンスの他のセッションにセッションをバインド解除、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 セッションをバインドすると、複数のセッションを同じトランザクションに含むことができ、ROLLBACK TRANSACTION または COMMIT TRANSACTION が実行されるまでロックを共有できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、複数のアクティブな結果セット (MARS) または分散トランザクションを使用してください。 詳細については、次を参照してください。[複数のアクティブな結果セットの使用 &#40;です。MARS &#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>引数  
 **'** *bind_token* **'**  
 トランザクションを識別する最初に取得されたトークンを使用して**sp_getbindtoken**または Open Data Services **srv_getbindtoken**関数。 *bind_token*は**varchar (255)**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 バインドされた 2 つのセッションが共有するのはトランザクションとロックだけです。 各セッションはそれぞれの分離レベルを保持し、一方のセッションで新しい分離レベルを設定しても、もう一方のセッションの分離レベルには影響しません。 各セッションは引き続きセキュリティ アカウントによって識別されます。またこれらのセッションは、そのアカウントに権限が与えられているデータベース リソースにしかアクセスできません。  
  
 **sp_bindsession**バインド トークンを使用して、2 つ以上の既存のクライアント セッションをバインドします。 これらのクライアント セッションがの同じインスタンスである必要があります、[!INCLUDE[ssDE](../../includes/ssde-md.md)]バインド トークンの取得元とします。 セッションとは、クライアントが実行しているコマンドのことです。 バインドされたデータベース セッションは、トランザクションとロック領域を共有します。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の 1 つのインスタンスから取得したバインド トークンは、DTC トランザクションの場合でも、別のインスタンスに接続するクライアント セッションには使用できません。 バインド トークンは、各インスタンス内でローカルに有効なだけで、複数のインスタンスにわたって共有することはできません。 別のインスタンス上のクライアント セッションをバインドする、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、実行して別のバインド トークンを取得する必要があります**sp_getbindtoken**です。  
  
 **sp_bindsession**はアクティブでないトークンを使用している場合は、エラーで失敗します。  
  
 使用するか、セッションからバインド解除**sp_bindsession**を指定せず*bind_token*内の NULL を渡すことにより*bind_token*です。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、指定したバインド トークンを現在のセッションにバインドします。  
  
> [!NOTE]  
>  例に示すバインド トークンを実行することによって取得した**sp_getbindtoken**実行する前に**sp_bindsession**です。  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_getbindtoken &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [srv_getbindtoken &#40;です。拡張ストアド プロシージャ API &#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
