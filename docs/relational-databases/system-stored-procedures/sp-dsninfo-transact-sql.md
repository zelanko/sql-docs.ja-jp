---
title: "sp_dsninfo (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4882ce3dd87c60f4fceaeb2b770c8879fadf3b78
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のサーバーと関連するディストリビューターから ODBC または OLE DB のデータ ソース情報を返します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>引数  
 [  **@dsn =**] **'***dsn***'**  
 ODBC DSN または OLE DB リンク サーバーの名前を指定します。 *dsn*は**varchar (128)**、既定値はありません。  
  
 [  **@infotype =**] **'***検査***'**  
 返される情報の種類です。 場合*検査*が指定されていないか、NULL を指定すると、すべての種類の情報が返されます。 *検査*は**varchar (128)**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**DBMS_NAME**|データ ソースのベンダーの名前を指定します。|  
|**DBMS_VERSION**|データ ソースのバージョンを指定します。|  
|**DATABASE_NAME**|データベース名を指定します。|  
|**SQL_SUBSCRIBER**|サブスクライバーにすることができるデータ ソースを指定します。|  
  
 [  **@login =**] **'***ログイン***'**  
 データ ソースのログインです。 データ ソースにログインが含まれる場合、NULL を指定するか、またはパラメーターを省略します。 *ログイン*は**varchar (128)**、既定値は NULL です。  
  
 [  **@password =**] **'***パスワード***'**  
 ログインのパスワードです。 データ ソースにログインが含まれる場合、NULL を指定するか、またはパラメーターを省略します。 *パスワード*は**varchar (128)**、既定値は NULL です。  
  
 [  **@dso_type=**]*ス*  
 データ ソースの種類を指定します。 *ス*は**int**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**1** (既定値)|ODBC データ ソース (ODBC data source)|  
|**3**|OLE DB データ ソース|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**情報の種類**|**nvarchar(64)**|DBMS_NAME、DBMS_VERSION、DATABASE_NAME、SQL_SUBSCRIBER などの情報の種類です。|  
|**値**|**nvarchar(512)**|関連する情報の種類の値です。|  
  
## <a name="remarks"></a>解説  
 **sp_dsninfo**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_dsninfo**レプリケーション、またはクエリを実行するデータベースを使用できるかどうかを示す ODBC または OLE DB のデータ ソース情報を取得します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dsninfo**です。  
  
## <a name="see-also"></a>参照  
 [sp_enumdsn &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
