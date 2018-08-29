---
title: sp_setnetname (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 71dcca516c1533c048d424e68d6aaae197d032ba
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024886"
---
# <a name="spsetnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ネットワーク名を設定**sys.servers**のリモート インスタンスの場合は、その実際のネットワーク コンピューター名に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 含むネットワーク名を持つコンピューターにリモート ストアド プロシージャ呼び出しの実行を有効にするこの手順を使用できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効な識別子です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>引数  
 **@server = '** *server* **'**  
 ユーザーが作成したリモート ストアド プロシージャ呼び出しの構文で参照しているリモート サーバーの名前を指定します。 1 行の**sys.servers**これを使用して既に存在する必要があります*server*します。 *server* のデータ型は **sysname**で、既定値はありません。  
  
 **@netname ='** *network_name* **'**  
 リモート ストアド プロシージャ呼び出しが行われるコンピューターのネットワーク名を指定します。 *network_name*は**sysname**、既定値はありません。  
  
 この名前は一致する必要があります、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コンピューターの名前と名前で許可されていない文字を含めることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 コンピューター名に無効な識別子が含まれている場合は、Windows コンピューターに対するリモート ストアド プロシージャの呼び出しで問題が生じることがあります。  
  
 リンク サーバーとリモート サーバーは同じ名前空間に存在するため、同じ名前にはできません。 ただし、定義できますリンク サーバーと特定のサーバーに対してリモート サーバーの両方を使用して別の名前を割り当てることで**sp_setnetname**うち 1 つのネットワーク名を基になるサーバーのネットワーク名に設定します。  
  
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
>  使用して**sp_setnetname**ローカル サーバーにリンク サーバーを指すはサポートされていません。 この方法で参照されたサーバーを分散トランザクションに加えることはできません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **sysadmin**と**setupadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例で使用される、一般的な管理順序[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を発行、リモート ストアド プロシージャの呼び出し。  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
