---
title: sp_help_agent_default (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_default
- sp_help_agent_default_TSQL
helpviewer_keywords:
- sp_help_agent_default
ms.assetid: 7ba55e39-05dd-43c7-b5da-b268ed8426dd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f92f64fe005bb49dd919f77e25931d5af025a8ea
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757873"
---
# <a name="sp_help_agent_default-transact-sql"></a>sp_help_agent_default (Transact-sql)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  パラメーターとして渡されたエージェント タイプについて、既定の構成の ID を取得します。 このストアド プロシージャは、任意のデータベース上のディストリビューター側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>引数  
`[ @profile_id = ] _profile_idOUTPUT`エージェントの種類の既定の構成の ID を設定します。 *profile_id*は**int**,、既定値はありません。*profile_id*は出力パラメーターでもあり、エージェントの種類の既定の構成の id を返します。  
  
`[ @agent_type = ] 'agent_type'`エージェントの種類を示します。 *agent_type*は**int**,、既定値はありませんが、これらの値のいずれかを指定することができます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|スナップショット エージェント。|  
|**2**|ログ リーダー エージェント。|  
|**3**|ディストリビューション エージェント。|  
|**4**|マージ エージェント。|  
|**9**|キュー リーダー エージェント (Queue Reader Agent)|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_help_agent_default**は、すべての種類のレプリケーションで使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_help_agent_default**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**replmonitor**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
