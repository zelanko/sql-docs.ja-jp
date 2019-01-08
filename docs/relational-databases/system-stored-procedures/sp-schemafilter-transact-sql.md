---
title: sp_schemafilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3018d23247a8f4d127d09878cb20c5f48f76c4ff
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206948"
---
# <a name="spschemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュできる Oracle テーブルを一覧表示するときに除外するスキーマの情報を変更および表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>引数  
 [**@publisher** =] **'***パブリッシャー***'**  
 以外の名前を指定します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [**@schema** =] **'***スキーマ***'**  
 スキーマの名前を指定します。 *スキーマ*は**sysname**既定値は NULL です。  
  
 [**@operation** =] **'***操作***'**  
 このスキーマで実行されるアクションです。 *操作*は**nvarchar (4)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**add**|指定されたスキーマを、パブリケーションに適さないスキーマの一覧に追加します。|  
|**drop**|指定されたスキーマを、パブリケーションに適さないスキーマの一覧から削除します。|  
|**ヘルプ**|パブリケーションに適さないスキーマの一覧を返します。|  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**スキーマ名**|**sysname**|パブリケーションに適さないスキーマの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_schemafilter**異種パブリッシャーのみに使用する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_schemafilter**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
