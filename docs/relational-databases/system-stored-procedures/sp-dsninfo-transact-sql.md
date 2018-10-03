---
title: sp_dsninfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93b8fb31c89d48a3281e5d5b102e94f95e5f2855
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828176"
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
 返される情報の種類です。 場合*検査*が指定されていないか、NULL を指定すると、あらゆる種類の情報が返されます。 *検査*は**varchar (128)**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
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
  
|値|説明|  
|-----------|-----------------|  
|**1** (既定値)|ODBC データ ソース (ODBC data source)|  
|**3**|OLE DB データ ソース|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**情報の種類**|**nvarchar(64)**|DBMS_NAME、DBMS_VERSION、DATABASE_NAME、SQL_SUBSCRIBER などの情報の種類です。|  
|**[値]**|**nvarchar(512)**|関連する情報の種類の値です。|  
  
## <a name="remarks"></a>コメント  
 **sp_dsninfo**はあらゆる種類のレプリケーションで使用します。  
  
 **sp_dsninfo**レプリケーションまたはクエリ、データベースを使用できるかどうかを示す ODBC または OLE DB のデータ ソース情報を取得します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dsninfo**します。  
  
## <a name="see-also"></a>参照  
 [sp_enumdsn &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
