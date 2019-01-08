---
title: sp_helpreplicationdboption (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29fcbe7f5e7b2b7e72c88390df9d5fe20c0f7352
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812034"
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
 [ **@dbname=**] **'***dbname***'**  
 データベースの名前です。 *dbname*は**sysname**、既定値は **%** します。 場合**%**、その結果、パブリッシャーのすべてのデータベースには、それ以外の場合、指定されたデータベースに関する情報のみが返されます。 ユーザーに適切な権限がないデータベースについての情報は返されません。詳細については以下を参照してください。  
  
 [  **@type=**] **'***型***'**  
 結果セットをいるデータベースのみに制限指定したレプリケーション オプション*型*値が有効になっています。 *型*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**発行**|トランザクション レプリケーションを許可します。|  
|**マージ パブリッシュします。**|マージ レプリケーションを許可します。|  
|**レプリケーションを許可**(既定値)|トランザクション レプリケーションまたはマージ レプリケーションを許可します。|  
  
 [  **@reserved=** ]*予約済み*  
 既存のパブリケーションとサブスクリプションに関する情報を返すかどうかを指定します。 *予約済み*は**ビット**既定値は 0 です。 場合**1**、結果セットに指定されたデータベースが任意の既存のパブリケーションまたはサブスクリプションにあるかどうかに関する情報が含まれています。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|データベースの名前です。|  
|**id**|**int**|データベースの識別子です。|  
|**transpublish**|**bit**|スナップショット パブリケーションまたはトランザクション パブリッシング; のデータベースを有効になっている場合値が**1**スナップショット パブリケーションまたはトランザクション パブリッシングが有効になっていることを意味します。|  
|**mergepublish**|**bit**|データベースがマージ パブリッシング; を有効になっている場合値が**1**マージ パブリッシュ方法を有効にします。|  
|**dbowner**|**bit**|ユーザーのメンバーである場合、 **db_owner**の値が、固定データベース ロール**1**ユーザーがこのロールのメンバーであることを示します。|  
|**dbreadonly**|**bit**|データベースが読み取り専用としてマークされているかどうかは、します。値が**1**データベースが読み取り専用であることを意味します。|  
|**haspublications**|**bit**|データベースに既存のパブリケーションがあります。値が**1**既存のパブリケーションがあることを意味します。|  
|**haspullsubscriptions**|**bit**|データベースにある既存のプル サブスクリプションです。値が**1**プル サブスクリプションがある、既存のことを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpreplicationdboption**スナップショット、トランザクション、およびマージ レプリケーションで使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバー、 **sysadmin**固定サーバー ロールが実行できる**sp_helpreplicationdboption**任意のデータベース。 メンバー、 **db_owner**固定データベース ロールが実行できる**sp_helpreplicationdboption**データベース。  
  
## <a name="see-also"></a>参照  
 [sp_replicationdboption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
