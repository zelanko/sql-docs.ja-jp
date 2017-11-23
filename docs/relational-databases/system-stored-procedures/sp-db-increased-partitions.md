---
title: "sp_db_increased_partitions |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs: TSQL
helpviewer_keywords: sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5266ce8c25465b6fd398111e7fd7e2d6634f5f34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したデータベースに最大 15, 000 のパーティションのサポートを有効または無効にします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて SP2 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 以降のバージョン)。 詳細については、次を参照してください[15,000 Partitions in SQL Server 2008 SP2 および SQL Server 2008 R2 SP1 のサポート](http://go.microsoft.com/fwlink/p/?LinkId=299658)、。|  
  
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
 指定したデータベースに対して 15, 000 個のパーティションのサポートを有効または無効にします。 *increased_partitions*は**varchar (6)**既定値は NULL です。 サポートを有効にするための承認済みの値は 'ON' または 'TRUE' です。サポートを無効にするための承認済みの値は 'OFF' または 'FALSE' です。 場合*increased_partitions*が指定されていない、プロシージャは指定されたデータベースのサポートが有効になっている、サポートを示すために 0 が無効になっているかを示す 1 を返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>Permissions  
 指定したデータベースに対する ALTER DATABASE 権限が必要です。  
  
  
