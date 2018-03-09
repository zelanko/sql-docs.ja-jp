---
title: "sp_getdefaultdatatypemapping (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db6ba2bdd02ed4ce9fe7b93132669d4f46ce40b9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したデータ型の間の既定のマッピングに関する情報を返します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース管理システム (DBMS)。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@source_dbms** =] **'***source_dbms***'**  
 データ型のマップ元となる DBMS の名前を指定します。 *source_dbms*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|ソースは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。|  
|**ORACLE**|マップ元は Oracle データベース。|  
  
 このパラメーターを指定する必要があります。  
  
 [  **@source_version=** ] **'***source_version***'**  
 マップ元 DBMS のバージョン番号を指定します。 *source_version*は**varchar (10)**既定値は NULL です。  
  
 [  **@source_type** =] **'***source_type***'**  
 マップ元 DBMS のデータ型です。 *source_type*は**sysname**、既定値はありません。  
  
 [  **@source_length=** ] *source_length*  
 マップ元 DBMS におけるデータ型の長さを指定します。 *source_length*は**bigint**既定値は NULL です。  
  
 [  **@source_precision=** ] *source_precision*  
 マップ元 DBMS におけるデータ型の有効桁数を指定します。 *source_precision*は**bigint**既定値は NULL です。  
  
 [  **@source_scale=** ] *source_scale*  
 マップ元 DBMS におけるデータ型の小数点以下桁数を指定します。 *source_scale*は**int**既定値は NULL です。  
  
 [  **@source_nullable=** ] *source_nullable*  
 マップ元 DBMS でデータ型が NULL の値をサポートするかどうかを指定します。 *source_nullable*は**ビット**、既定値は**1**NULL 値がサポートされていることを意味します。  
  
 [  **@destination_dbms**  =] **'***destination_dbms***'**  
 マップ先 DBMS の名前です。 *destination_dbms*は**sysname**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|マップ先は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース。|  
|**ORACLE**|マップ先は Oracle データベース。|  
|**DB2**|マップ先は IBM DB2 データベース。|  
|**SYBASE**|マップ先は Sybase データベース。|  
  
 このパラメーターを指定する必要があります。  
  
 [  **@destination_version** =] **'***destination_version***'**  
 マップ先 DBMS の製品バージョンを指定します。 *destination_version*は**varchar (10)**既定値は NULL です。  
  
 [  **@destination_type** =] **'***destination_type***'**出力  
 マップ先 DBMS で定義されているデータ型を指定します。 *destination_type*は**sysname**既定値は NULL です。  
  
 [  **@destination_length=** ] *destination_length*出力  
 マップ先 DBMS でのデータ型の長さ指定します。 *destination_length*は**bigint**既定値は NULL です。  
  
 [  **@destination_precision=** ] *destination_precision*出力  
 マップ先 DBMS でのデータ型の有効桁数を指定します。 *destination_precision*は**bigint**既定値は NULL です。  
  
 [  **@destination_scale=** ] *destination_scale***出力**  
 マップ先 DBMS でのデータ型の小数点以下桁数を指定します。 *destination_scale*は**int**既定値は NULL です。  
  
 [  **@destination_nullable=** ] *destination_nullable***出力**  
 マップ先 DBMS でデータ型が NULL の値をサポートするかどうかを指定します。 *destination_nullable*は**ビット**既定値は NULL です。 **1** NULL 値がサポートされていることを意味します。  
  
 [  **@dataloss=** ]*データ消失***出力**  
 マッピングでデータ損失の可能性があるかどうかを示します。 *データ消失*は**ビット**既定値は NULL です。 **1**データ損失の可能性があることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_getdefaultdatatypemapping**間のレプリケーションのすべての種類で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DBMS します。  
  
 **sp_getdefaultdatatypemapping**となる、既定のマッピング先データ型指定されたソースのデータ型に最も近い一致を返します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_getdefaultdatatypemapping**です。  
  
## <a name="see-also"></a>参照  
 [sp_helpdatatypemap &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle サブスクライバー](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
