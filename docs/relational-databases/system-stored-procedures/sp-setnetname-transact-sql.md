---
title: "sp_setnetname (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e9f439854cc1d3af3ca5db09981f2eba2af7a4f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spsetnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ネットワーク名を設定**sys.servers**リモート インスタンスの場合、実際のネットワーク コンピューターの名前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 含むネットワーク名を持つコンピューターをリモート ストアド プロシージャ呼び出しの実行を有効にするこの手順を使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子が無効です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>引数  
 **@server= '** *サーバー* **'**  
 ユーザーが作成したリモート ストアド プロシージャ呼び出しの構文で参照しているリモート サーバーの名前を指定します。 内のただ 1 つの行**sys.servers**これを使用する存在していなければなりません*サーバー*です。 *server* のデータ型は **sysname**で、既定値はありません。  
  
 **@netname='** *network_name* **'**  
 リモート ストアド プロシージャ呼び出しが行われるコンピューターのネットワーク名を指定します。 *network_name*は**sysname**、既定値はありません。  
  
 この名前は一致する必要があります、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コンピューター名、および名前で許可されていない文字を含めることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 コンピューター名に無効な識別子が含まれている場合は、Windows コンピューターに対するリモート ストアド プロシージャの呼び出しで問題が生じることがあります。  
  
 リンク サーバーとリモート サーバーは同じ名前空間に存在するため、同じ名前にはできません。 ただし、定義できます、リンク サーバーと特定のサーバーに対してリモート サーバーの両方を使用して別の名前を割り当てることによって**sp_setnetname**うちの 1 つのネットワーク名を基になるサーバーのネットワーク名に設定します。  
  
```  
--Assume sqlserv2 is actual name of SQL Server   
--database server  
EXEC sp_addlinkedserver 'sqlserv2';  
GO  
EXEC sp_addserver 'rpcserv2';  
GO  
EXEC sp_setnetname 'rpcserv2', 'sqlserv2';  
```  
  
> [!NOTE]  
>  使用して**sp_setnetname**ローカル サーバーへのリンク サーバーをポイントすることはできません。 この方法で参照されたサーバーを分散トランザクションに加えることはできません。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **sysadmin**と**setupadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例で使用される一般的な管理順序[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を発行、リモート ストアド プロシージャの呼び出しです。  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
