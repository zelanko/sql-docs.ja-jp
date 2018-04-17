---
title: OLE オートメーション ストアド プロシージャ (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], OLE Automation
- OLE Automation [SQL Server], stored procedures
ms.assetid: ff16a833-01fe-4877-8aa6-55b72603ec2e
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3ba62cfd39d2f0f24dac75d4cebf4601358159ae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ole-automation-stored-procedures-transact-sql"></a>OLE オートメーション ストアド プロシージャ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内で OLE オートメーション オブジェクトを使用するために、次のシステム ストアド プロシージャが用意されています。 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は OLE オートメーション ストアド プロシージャへのアクセスをブロックします。これは、このコンポーネントがサーバーのセキュリティ構成の中で無効になっているためです。 システム管理者は、sp_configure を使用して、OLE オートメーション プロシージャへのアクセスを有効にできます。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
|||  
|-|-|  
|[sp_OACreate](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md)|[sp_OAMethod](../../relational-databases/system-stored-procedures/sp-oamethod-transact-sql.md)|  
|[sp_OADestroy](../../relational-databases/system-stored-procedures/sp-oadestroy-transact-sql.md)|[sp_OASetProperty](../../relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql.md)|  
|[sp_OAGetErrorInfo](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)|[sp_OAStop](../../relational-databases/system-stored-procedures/sp-oastop-transact-sql.md)|  
|[sp_OAGetProperty](../../relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql.md)|[オブジェクト階層構文 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
