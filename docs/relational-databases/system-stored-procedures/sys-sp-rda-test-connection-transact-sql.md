---
title: sys.sp_rda_test_connection (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cdf171c66c19d87ea4919eeb55dca65f14b89ebd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982877"
---
# <a name="syssprdatestconnection-transact-sql"></a>sys.sp_rda_test_connection (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  SQL Server から、リモート Azure サーバーへの接続をテストし、データの移行を妨げる可能性のある問題を報告します。  
  
## <a name="syntax"></a>構文  
  
```  
  
EXECUTE sys.sp_rda_test_connection  
   @database_name = N'db_name',   
   @server_address = N'azure_server_fully_qualified_address',  
   @azure_username = N'azure_username',   
   @azure_password = N'azure_password',  
   @credential_name = N'credential_name'  
  
```  
  
## <a name="arguments"></a>引数  
 @database_name = N'*db_name*'  
 Stretch 対応 SQL Server データベースの名前。 このパラメーターはオプションです。  
  
 @server_address = N'*azure_server_fully_qualified_address*'  
 Azure のサーバーの完全修飾アドレス。  
  
-   値を指定する場合 **@database_name** 、指定されたデータベースで Stretch 対応はありませんが、その値を指定する必要がある **@server_address** します。  
  
-   値を指定する場合 **@database_name** の値を指定する必要はありませんし、指定されたデータベースが Stretch 有効になっている **@server_address** します。 値を指定する場合 **@server_address** Stretch 対応データベースに関連付けられている既存の Azure サーバーを既に使用や、ストアド プロシージャでは無視されます。  
  
 @azure_username = N'*azure_username*  
 リモート Azure サーバーのユーザー名。  
  
 @azure_password = N'*azure_password*'  
 リモート Azure サーバーのパスワード。  
  
 @credential_name = N'*credential_name*'  
 ユーザー名とパスワードを指定すると、代わりに、Stretch 対応データベースに格納されている資格情報の名前を行うことができます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 場合に**成功**sp_rda_test_connection EX_INFO 重大度を持つエラー 14855 (STRETCH_MAJOR、STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) を返します、成功コードが返されます。  
  
 場合に**エラー**sp_rda_test_connection EX_USER 重大度を持つエラー 14856 (STRETCH_MAJOR、STRETCH_CONNECTION_TEST_PROC_FAILED) を返します、エラーには、コードが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|link_state|ssNoversion|値に対応して、次の値のいずれかの**link_state_desc**します。<br /><br /> -   0<br />-   1<br />-   2<br />-   3<br />-   4|  
|link_state_desc|varchar (32)|上記に対応して、次の値のいずれかの値**link_state**します。<br /><br /> -正常<br />     SQL サーバーとリモート Azure サーバーが正常な状態です。<br />-   ERROR_AZURE_FIREWALL<br />     Azure のファイアウォールには、SQL Server とリモート Azure サーバー間のリンクが原因です。<br />-   ERROR_NO_CONNECTION<br />     SQL Server では、リモート Azure サーバーへの接続を作成できません。<br />-   ERROR_AUTH_FAILURE<br />     認証の失敗が原因で SQL Server とリモート Azure サーバー間のリンク。<br />-エラー<br />     認証の問題、接続の問題またはファイアウォールの問題でないエラーが SQL Server とリモート Azure サーバー間のリンクを妨げています。|  
|error_number|ssNoversion|エラーの数。 エラーがない場合は、このフィールドは NULL です。|  
|error_message|nvarchar(1024)|エラー メッセージです。 エラーがない場合は、このフィールドは NULL です。|  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>SQL Server から、リモート Azure サーバーへの接続を確認してください。  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 結果は、SQL Server が、リモート Azure サーバーに接続できないことを示します。  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<接続に関連するエラー番号 >*|*\<接続に関連するエラー メッセージ >*|  
  
### <a name="check-the-azure-firewall"></a>Azure のファイアウォールを確認します。  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 結果は、Azure のファイアウォールが SQL Server とリモート Azure サーバー間のリンクを拒否されているを表示します。  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<ファイアウォールに関連するエラー番号 >*|*\<ファイアウォールに関連するエラー メッセージ >*|  
  
### <a name="check-authentication-credentials"></a>認証の資格情報を確認してください。  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 結果は、SQL Server とリモート Azure サーバー間のリンクを認証の失敗が拒否されているを表示します。  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<認証に関連するエラー番号 >*|*\<authentication-related error message>*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>リモート Azure サーバーの状態を確認してください。  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 結果は、接続が正常であると、指定したデータベースの Stretch Database を有効にできることを示します。  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
