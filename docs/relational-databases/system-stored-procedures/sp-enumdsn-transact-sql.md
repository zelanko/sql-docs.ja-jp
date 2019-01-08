---
title: sp_enumdsn (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords:
- sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f58a16b3d4d393a94dc5e42413ddfeb2a8eb5d9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52773894"
---
# <a name="spenumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントで実行中のサーバーに定義されている、すべての ODBC および OLE DB のデータ ソース名の一覧を返します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**データ ソース名**|**sysname**|データ ソースの名前。|  
|**[説明]**|**varchar(255)**|データ ソースの説明です。|  
|**型**|**int**|データ ソースの種類です。<br /><br /> **1** = ODBC DSN<br /><br /> **3** = OLE DB データ ソース|  
|**プロバイダー名**|**varchar(255)**|OLE DB プロバイダーの名前です。 ODBC DSN の場合、値は NULL です。|  
  
## <a name="remarks"></a>コメント  
 すべて[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスがユーザーのコンテキスト。 ユーザー コンテキストは、そのユーザーの ODBC データ ソースの定義を含むレジストリ エントリの集合です。 ユーザー コンテキストは実行中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] におけるユーザー名により提供されます。  
  
 たとえば、サーバーがシステム アカウントのユーザー コンテキストで実行されている場合は、返されるデータ ソース名 (DSN) はシステム アカウントに関連付けられているすべてのシステム DSN です。 サーバーがプライベートなユーザー アカウントで実行されている場合は、そのユーザーのプライベート アカウントで定義された DSN だけが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_enumdsn**します。  
  
## <a name="see-also"></a>参照  
 [sp_dsninfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
