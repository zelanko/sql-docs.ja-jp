---
title: "sp_schemafilter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords: sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 635a9d8fc39ea3621c4ba9b11f54300c19ec1011
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
 [ **@publisher**  =] **'***パブリッシャー***'**  
 以外の名前を指定します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@schema**  =] **'***スキーマ***'**  
 スキーマの名前を指定します。 *スキーマ*は**sysname**既定値は NULL です。  
  
 [ **@operation**  =] **'***操作***'**  
 このスキーマで実行されるアクションです。 *操作*は**nvarchar (4)**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**追加**|指定されたスキーマを、パブリケーションに適さないスキーマの一覧に追加します。|  
|**ドロップ**|指定されたスキーマを、パブリケーションに適さないスキーマの一覧から削除します。|  
|**ヘルプ**|パブリケーションに適さないスキーマの一覧を返します。|  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**スキーマ名**|**sysname**|パブリケーションに適さないスキーマの名前です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_schemafilter**異種パブリッシャーでのみ使用する必要があります。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_schemafilter**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
