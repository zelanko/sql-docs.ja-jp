---
title: "sys.linked_logins (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs: TSQL
helpviewer_keywords: sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ca2137294edf7a24c0ad5b167c5e1037a86cab1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リンク サーバー ログイン マッピングごとに 1 行のデータを返します。この情報は、ローカル サーバーから対応するリンク サーバーへの、RPC と分散クエリで使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|内のサーバーの ID **sys.servers**です。|  
|**local_principal_id**|**int**|マッピングが適用されるサーバー プリンシパル。<br /><br /> 0 = ワイルドカードまたは public。|  
|**uses_self_credential**|**bit**|1 の場合、セッションで固有の資格情報を使用。0 の場合、セッションで与えられた名前とパスワードを使用。|  
|**remote_name**|**sysname**|接続時に使用するリモート ユーザー名。 パスワードも格納されますが、カタログ ビューのインターフェイスには表示されません。|  
|**modify_date**|**datetime**|リンク ログインが前回変更された日付。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [リンク サーバーのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
