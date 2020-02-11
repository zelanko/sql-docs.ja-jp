---
title: sp_enumdsn (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: d84d366483cd5a887eb299b0f8d9208998e835c1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124590"
---
# <a name="sp_enumdsn-transact-sql"></a>sp_enumdsn (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントで実行中のサーバーに定義されている、すべての ODBC および OLE DB のデータ ソース名の一覧を返します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**データソース名**|**sysname**|データソースの名前。|  
|**説明**|**varchar (255)**|データ ソースの説明です。|  
|**Type**|**int**|データ ソースの種類です。<br /><br /> **1** = ODBC DSN<br /><br /> **3** = データソースの OLE DB|  
|**プロバイダー名**|**varchar (255)**|OLE DB プロバイダーの名前です。 ODBC DSN の場合、値は NULL です。|  
  
## <a name="remarks"></a>解説  
 すべて[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービスにユーザーコンテキストがあります。 ユーザーコンテキストは、ユーザーの ODBC データソースの定義を含むレジストリエントリのセットです。 ユーザーコンテキストは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されているユーザー名によって提供されます。  
  
 たとえば、サーバーがシステムアカウントのユーザーコンテキストで実行されている場合、返されるデータソース名 (Dsn) はすべて、システムアカウントに関連付けられているシステム Dsn になります。 サーバーがプライベートユーザーアカウントで実行されている場合は、そのユーザーのそのプライベートアカウントに対して定義されている Dsn だけが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_enumdsn**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_dsninfo &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
