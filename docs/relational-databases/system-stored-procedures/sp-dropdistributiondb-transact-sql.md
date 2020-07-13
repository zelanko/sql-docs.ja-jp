---
title: sp_dropdistributiondb (Transact-sql) |Microsoft Docs
description: 別のデータベースで使用されていないディストリビューションデータベースとファイルを削除します。 このストアドプロシージャは、ディストリビューター側で任意のデータベースに対して実行されます。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistributiondb_TSQL
- sp_dropdistributiondb
helpviewer_keywords:
- sp_dropdistributiondb
ms.assetid: b6dd1846-2259-4d29-93af-a70a5d25a0c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9d9290b02c149889a488452d71ae800134d38f00
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786967"
---
# <a name="sp_dropdistributiondb-transact-sql"></a>sp_dropdistributiondb (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  ディストリビューションデータベースを削除します。 別のデータベースで使用されていない場合に、データベースによって使用されている物理ファイルを削除します。 このストアドプロシージャは、ディストリビューター側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdistributiondb [ @database= ] 'database'  
```  
  
## <a name="arguments"></a>引数  
`[ @database = ] 'database'`削除するデータベースを示します。 *データベースのデータ*型は**sysname**で、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_dropdistributiondb**は、すべての種類のレプリケーションで使用されます。  
  
 **Sp_dropdistributor**を実行してディストリビューターを削除する前に、このストアドプロシージャを実行する必要があります。  
  
 **sp_dropdistributiondb**は、ディストリビューションデータベースのキューリーダーエージェントジョブが存在する場合にも削除します。  
  
 ディストリビューションを無効にするには、ディストリビューションデータベースがオンラインである必要があります。 ディストリビューションデータベースに対してデータベーススナップショットが存在する場合は、ディストリビューションを無効にする前に削除する必要があります。 データベーススナップショットは、データベースの読み取り専用のオフラインコピーであり、レプリケーションスナップショットに関連付けられていません。 詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributiondb-tr_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_dropdistributiondb**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [パブリッシングおよびディストリビューションを無効にする](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributiondb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
