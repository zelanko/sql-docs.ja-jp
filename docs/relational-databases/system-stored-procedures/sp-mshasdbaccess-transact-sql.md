---
title: sp_MShasdbaccess (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_MShasdbaccess
- sp_MShasdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_MShasdbaccess
ms.assetid: a9a23b90-2c60-4460-80a7-d7e14cc5a6a8
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3cfaa25b0595a809e6c505f6c0a487a501562b0a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spmshasdbaccess-transact-sql"></a>sp_MShasdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザーがアクセスできるすべてのデータベースの名前と所有者を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_MShasdbaccess      
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 実行する権限が与えられて、**パブリック**ロール。  
  
## <a name="see-also"></a>参照  
 [sys.sysdatabases &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)  
  
  
