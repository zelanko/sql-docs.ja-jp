---
description: sp_syscollector_set_warehouse_instance_name (Transact-sql)
title: sp_syscollector_set_warehouse_instance_name (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_warehouse_instance_name_TSQL
- sp_syscollector_set_warehouse_instance_name
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_warehouse_instance_name
ms.assetid: 5320fcd4-bed1-468f-b784-a5e10fcfaeb6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86816adb5b3683aa6cbcd5c869b233960cf1a68f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493005"
---
# <a name="sp_syscollector_set_warehouse_instance_name-transact-sql"></a>sp_syscollector_set_warehouse_instance_name (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  管理データウェアハウスへの接続に使用する接続文字列のインスタンス名を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_set_warehouse_instance_name [ @instance_name = ] 'instance_name'  
```  
  
## <a name="arguments"></a>引数  
 [ @instance_name =] '*instance_name*'  
 インスタンス名を指定します。 *instance_name* は **sysname** であり、NULL の場合は既定でローカルインスタンスに設定されます。  
  
> **注:**_instance_name_は、コンピューター名と、 *computerName*instanceName という形式のインスタンス名で構成される完全修飾インスタンス名である必要があります \\ *instanceName*。    
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="remarks"></a>解説  
 データコレクター全体の構成を変更する前に、データコレクターを無効にする必要があります。 データコレクターが有効になっている場合、このプロシージャは失敗します。  
  
 現在のインスタンス名を表示するには、 [syscollector_config_store](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md) システムビューに対してクエリを実行します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行するには、dc_admin (EXECUTE 権限を持つ) 固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、リモート サーバー上の管理データ ウェアハウスのインスタンスを使用するようにデータ コレクターを構成する方法を示します。 この例において、リモート サーバーの名前は `RemoteSERVER` で、データベースは既定のインスタンスにインストールされています。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_set_warehouse_instance_name N'RemoteSERVER'; -- the default instance is assumed on the remote server  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)  
  
  
