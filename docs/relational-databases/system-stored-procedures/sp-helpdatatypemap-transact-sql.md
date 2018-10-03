---
title: sp_helpdatatypemap (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e1eab8424e2ff5eb81e8d89a6ed897b7d19b5b72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837940"
---
# <a name="sphelpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  間の定義済みのデータ型マッピングに関する情報を返します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース管理システム (DBMS)。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
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
  
|値|説明|  
|-----------|-----------------|  
|**MSSQLSERVER**|ソースが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。|  
|**ORACLE**|マップ元は Oracle データベース。|  
  
 [ **@source_version**=] **'***source_version***'**  
 マップ元 DBMS の製品バージョンです。 *source_version*は**varchar (10)** を指定しない場合、データの型マッピング DBMS が返される、ソースのすべてのバージョン。 値を指定した場合は、マップ元 DBMS のバージョンによって結果セットがフィルター選択されます。  
  
 [ **@source_type**=] **'***source_type***'**  
 マップ元 DBMS で定義されているデータ型です。 *source_type*は**sysname**、指定されていない場合のマップ元 DBMS でのすべてのデータ型マッピングが返されます。 値を指定した場合は、マップ元 DBMS のデータ型によって結果セットがフィルター選択されます。  
  
 [ **@destination_dbms** =] **'***destination_dbms***'**  
 マップ先 DBMS の名前です。 *destination_dbms*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
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
 既定のデータ型マッピングのみを返すかどうかを示します。 *defaults_only*は**ビット**、既定値は**0**します。 **1**とする、のみの既定のデータ型マッピングが返されます。 **0**と既定値と、ユーザー定義データ型のマッピングが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|説明|  
|-----------------|-----------------|  
|**mapping_id**|データ型マッピングを識別します。|  
|**source_dbms**|マップ元 DBMS の名前とバージョン番号です。|  
|**source_type**|マップ元 DBMS のデータ型です。|  
|**destination_dbms**|マップ先 DBMS の名前です。|  
|**destination_type**|マップ先 DBMS のデータ型です。|  
|**is_default**|既定のマッピングか既定以外のマッピングかを示します。 値**0**このマッピングがユーザー定義であることを示します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpdatatypemap**から SQL Server 以外のパブリッシャーとの両方からのデータ型マッピングを定義します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に以外のパブリッシャーを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。  
  
 指定したソースとマップ先 DBMS の組み合わせがサポートされていない場合**sp_helpdatatypemap**空の結果セットを返します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**のメンバー、またはディストリビューターの固定サーバー ロール、 **db_owner** 、ディストリビューション データベースの固定データベース ロールが実行できる**sp_helpdatatypemap**.  
  
## <a name="see-also"></a>参照  
 [sp_getdefaultdatatypemapping &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
