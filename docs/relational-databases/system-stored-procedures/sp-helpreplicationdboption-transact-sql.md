---
title: "sp_helpreplicationdboption (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords: sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d53bf08bf26d8682093d72e55f290701d0b3c625
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャー側のデータベースでレプリケーションが有効になっているかどうかを示します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。 *Oracle パブリッシャーに対してはサポートされていません。*  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@dbname=**] **'***dbname***'**  
 データベースの名前です。 *dbname*は**sysname**、既定値は **%**です。 場合 **%** 、その結果セットには、パブリッシャーのすべてのデータベースが含まれています、それ以外の場合、指定されたデータベースに関する情報のみが返されます。 ユーザーに適切な権限がないデータベースについての情報は返されません。詳細については以下を参照してください。  
  
 [  **@type=**] **'***型***'**  
 結果セットを含まれているデータベースのみに制限、指定したレプリケーション オプション*型*値が有効になっています。 *型*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**発行**|トランザクション レプリケーションを許可します。|  
|**マージ パブリッシュします。**|マージ レプリケーションを許可します。|  
|**レプリケーションを許可**(既定値)|トランザクション レプリケーションまたはマージ レプリケーションを許可します。|  
  
 [  **@reserved=** ]*予約済み*  
 既存のパブリケーションとサブスクリプションに関する情報を返すかどうかを指定します。 *予約済み*は**ビット**既定値は 0 です。 場合**1**、結果セットには、既存のパブリケーションまたはサブスクリプションに指定されたデータベースがあるかどうかに関する情報が含まれています。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|データベースの名前です。|  
|**id**|**int**|データベースの識別子です。|  
|**transpublish**|**bit**|スナップショット パブリケーションまたはトランザクション パブリッシング; のデータベースを有効になっている場合値が**1**スナップショット パブリケーションまたはトランザクション パブリッシングが有効になっていることを意味します。|  
|**mergepublish**|**bit**|マージ パブリッシング; のデータベースが有効にされている場合値が**1**マージ パブリッシュすることを意味が有効にします。|  
|**dbowner**|**bit**|ユーザーのメンバーである場合、 **db_owner**値が、固定データベース ロールの場合は; **1**ユーザーがこのロールのメンバーであることを示します。|  
|**dbreadonly**|**bit**|データベースが読み取り専用としてマークされているかどうかは、します。値が**1**データベースが読み取り専用であることを意味します。|  
|**haspublications**|**bit**|データベースにあるすべての既存のパブリケーション値が**1**既存のパブリケーションがあることを意味します。|  
|**haspullsubscriptions**|**bit**|データベースにある既存のプル サブスクリプションです。値が**1**ことは既存のプル サブスクリプションを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpreplicationdboption**はスナップショット、トランザクション、およびマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバー、 **sysadmin**固定サーバー ロールが実行できる**sp_helpreplicationdboption**任意のデータベースにします。 メンバー、 **db_owner**固定データベース ロールが実行できる**sp_helpreplicationdboption**データベース。  
  
## <a name="see-also"></a>参照  
 [sp_replicationdboption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
