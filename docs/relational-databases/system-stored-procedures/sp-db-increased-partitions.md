---
title: sp_db_increased_partitions |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7692f214c38d4d1925b96390f99fa9d86675f8ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したデータベースに最大 15, 000 のパーティションのサポートを有効または無効にします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>引数  
 [ @dbname=] '*database_name*'  
 データベースの名前です。 *dbname*は**sysname**で、既定値は NULL です。 場合*dbname*が指定されていない、現在のデータベースを使用します。  
  
 [ @increased_partitions=] '*increased_partitions*'  
 指定したデータベースに対して 15, 000 個のパーティションのサポートを有効または無効にします。 *increased_partitions*は**varchar (6)** 既定値は NULL です。 サポートを有効にするための承認済みの値は 'ON' または 'TRUE' です。サポートを無効にするための承認済みの値は 'OFF' または 'FALSE' です。 場合*increased_partitions*が指定されていない、プロシージャは指定されたデータベースのサポートが有効になっている、サポートを示すために 0 が無効になっているかを示す 1 を返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 指定したデータベースに対する ALTER DATABASE 権限が必要です。  
  
  
