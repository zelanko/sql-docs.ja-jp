---
title: linked_logins (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3182516451f88d25bbd2d6e1e08884f638dea02c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783974"
---
# <a name="syslinked_logins-transact-sql"></a>linked_logins (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  ローカルサーバーから対応するリンクサーバーへの RPC および分散クエリで使用するために、リンクサーバーのログインマッピングごとに1行の値を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|**サーバーの ID です。**|  
|**local_principal_id**|**int**|マッピングが適用されるサーバー プリンシパル。<br /><br /> 0 = ワイルドカードまたは public。|  
|**uses_self_credential**|**bit**|1の場合、マッピングはセッションが独自の資格情報を使用する必要があることを示します。それ以外の場合、0は、セッションが指定された名前とパスワードを使用することを示します。|  
|**remote_name**|**sysname**|接続時に使用するリモートユーザー名。 パスワードも保存されますが、カタログビューインターフェイスでは公開されません。|  
|**modify_date**|**datetime**|リンクログインが最後に変更された日付。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [リンクサーバーのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
