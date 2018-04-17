---
title: sp_helpdatatypemap (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e594c9b1d13730df2ccc93bf04d0348a5d2175b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  間に定義されたデータ型マッピングに関する情報を返します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース管理システム (DBMS)。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@source_dbms**=] **'***source_dbms***'**  
 データ型のマップ元となる DBMS の名前を指定します。 *source_dbms*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|ソースは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。|  
|**ORACLE**|マップ元は Oracle データベース。|  
  
 [ **@source_version**=] **'***source_version***'**  
 マップ元 DBMS の製品バージョンです。 *source_version*は**varchar (10)**、指定されていない場合、データの型マッピング DBMS を返すソースのすべてのバージョン。 値を指定した場合は、マップ元 DBMS のバージョンによって結果セットがフィルター選択されます。  
  
 [ **@source_type**=] **'***source_type***'**  
 マップ元 DBMS で定義されているデータ型です。 *source_type*は**sysname**、指定されていない場合のマップ元 DBMS でのすべてのデータ型マッピングが返されます。 値を指定した場合は、マップ元 DBMS のデータ型によって結果セットがフィルター選択されます。  
  
 [ **@destination_dbms** =] **'***destination_dbms***'**  
 マップ先 DBMS の名前です。 *destination_dbms*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|マップ先は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース。|  
|**ORACLE**|マップ先は Oracle データベース。|  
|**DB2**|マップ先は IBM DB2 データベース。|  
|**SYBASE**|マップ先は Sybase データベース。|  
  
 [ **@destination_version**=] **'***destination_version***'**  
 マップ先 DBMS の製品バージョンを指定します。 *destination_version*は**varchar (10)**、マップ先 DBMS のすべてのバージョンのマッピングが返されますが指定されていない場合。 値を指定した場合は、マップ先 DBMS のバージョンによって結果セットがフィルター選択されます。  
  
 [ **@destination_type**=] **'***destination_type***'**  
 マップ先 DBMS で定義されているデータ型を指定します。 *destination_type*は**sysname**、指定されていない場合のマップ先 DBMS でのすべてのデータ型マッピングが返されます。 値を指定した場合は、マップ先 DBMS のデータ型によって結果セットがフィルター選択されます。  
  
 [ **@defaults_only**=] *defaults_only*  
 既定のデータ型マッピングのみを返すかどうかを示します。 *defaults_only*は**ビット**、既定値は**0**します。 **1**ことを意味するのみの既定のデータ型マッピングが返されます。 **0**ことを意味する、既定およびすべてのユーザー定義データ型マッピングが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|Description|  
|-----------------|-----------------|  
|**mapping_id**|データ型マッピングを識別します。|  
|**source_dbms**|マップ元 DBMS の名前とバージョン番号です。|  
|**source_type**|マップ元 DBMS のデータ型です。|  
|**destination_dbms**|マップ先 DBMS の名前です。|  
|**destination_type**|マップ先 DBMS のデータ型です。|  
|**is_default**|既定のマッピングか既定以外のマッピングかを示します。 値**0**このマッピングがユーザー定義であることを示します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpdatatypemap**から SQL Server 以外のパブリッシャーとの両方からのデータ型マッピングを定義[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外のパブリッシャー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 指定したソースとマップ先 DBMS の組み合わせがサポートされていないとき**sp_helpdatatypemap**は空の結果セットを返します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner**ディストリビューション データベースの固定データベース ロールが実行できる**sp_helpdatatypemap**.  
  
## <a name="see-also"></a>参照  
 [sp_getdefaultdatatypemapping &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
