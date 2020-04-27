---
title: SQL Server 2014 | のデータベースエンジン廃止された機能Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2ebb9b4e3db7cf8f7a19fd582dceb0b19f5c47d0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67463465"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a>SQL Server 2014 で廃止されたデータベース エンジンの機能
  このトピックでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] で使用できなくなった [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。  
  
## <a name="discontinued-features-in-sssql14"></a><a name="SQL14"></a>で廃止された機能[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] で削除された機能を次の表に示します。  
  
|カテゴリ|廃止された機能|代替|  
|--------------|--------------------------|-----------------|  
|互換性レベル|90互換性レベル|データベースを互換性レベル 100 以上に設定する必要があります。 互換性レベル 100 未満のデータベースを [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] にアップグレードすると、データベースの互換性レベルはアップグレード操作中に 100 に設定されます。|  
  
## <a name="discontinued-features-in-sssql11"></a><a name="Denali"></a>で廃止された機能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] で削除された機能を次の表に示します。  
  
|カテゴリ|廃止された機能|代替|  
|--------------|--------------------------|-----------------|  
|バックアップと復元|**Backup {database &#124; log} WITH PASSWORD**および**backup {database &#124; LOG} with MEDIAPASSWORD**は廃止されました。 **[MEDIA] を使用した復元 {DATABASE &#124; LOG}** は、引き続き非推奨とされます。|None|  
|バックアップと復元|**復元 {データベース &#124; ログ}...DBO_ONLY**|**{DATABASE &#124; LOG} を復元します......RESTRICTED_USER**|  
|互換性レベル|80互換性レベル|データベースは、互換性レベル90以上に設定する必要があります。|  
|構成オプション|`sp_configure 'user instance timeout'` および `'user instances enabled'`|ローカル データベースの機能を使用します。 詳細については、「 [SqlLocalDB Utility](../tools/sqllocaldb-utility.md) 」を参照してください。|  
|接続プロトコル|VIA プロトコルのサポートは中止されました。|代わりに TCP を使用してください。|  
|データベース オブジェクト|トリガーでの `WITH APPEND` 句の使用|トリガー全体を再作成してください。|  
|データベース オプション|`sp_dboption`|`ALTER DATABASE`|  
|Mail|SQL Mail|データベース メールを使用してください。 詳細については、「 [SQL Mail の代わりにデータベースメール](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md)を[データベースメール](../relational-databases/database-mail/database-mail.md)して使用する」を参照してください。|  
|メモリ管理|32 ビットの AWE (Address Windowing Extensions) と 32 ビットのホット アド メモリ サポート。|64 ビットのオペレーティング システムを使用します。|  
|メタデータ|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|プログラミング|SQL Server 分散管理オブジェクト (SQL-DMO)。|SQL Server 管理オブジェクト (SMO)|  
|クエリヒント|`FASTFIRSTROW` ヒント|`OPTION (FAST`*n* `)`。|  
|リモート サーバー|`sp_addserver` を使用して新しいリモート サーバーを作成する機能は廃止されました。 'local' オプションを設定した `sp_addserver` は引き続き使用できます。 アップグレード中に保持されたリモート サーバーまたはレプリケーションによって作成されたリモート サーバーは使用可能です。|リンク サーバーを使用してリモート サーバーを置き換えてください。|  
|Security|`sp_dropalias`|別名をユーザー アカウントとデータベース ロールの組み合わせで置き換えてください。 アップグレードされたデータベースで別名を削除するには、`sp_dropalias` を使用します。|  
|Security|2000より[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]前のログインの値を表す**pwdcompare**のバージョンパラメーターは廃止されました。|None|  
|SMO での Service Broker のプログラミング|**IObjectPermission**インターフェイスは、**このクラスに**よって実装されなくなりました。このクラスを実装すると、||  
|SET オプション|`SET DISABLE_DEF_CNST_CHK`|なし。|  
|システム テーブル|sys.database_principal_aliases|別名の代わりにロールを使用してください。|  
|Transact-SQL|`RAISERROR` という形式の `RAISERROR integer 'string'` は廃止されました。|現在の**RAISERROR (...)** 構文を使用してステートメントを書き直してください。|  
|Transact-SQL 構文|`COMPUTE / COMPUTE BY`|`ROLLUP` を使用します|  
|Transact-SQL 構文|および** \* ** **=&#42;** の使用|ANSI 結合構文を使用してください。 詳細については、「 [FROM (transact-sql)](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx) 」を参照してください。|  
|XEvent|databases_data_file_size_changed、databases_log_file_size_changed<br /><br /> eventdatabases_log_file_used_size_changed<br /><br /> locks_lock_timeouts_greater_than_0<br /><br /> locks_lock_timeouts|次の各イベントに置き換えられました: database_file_size_change、database_file_size_change<br /><br /> database_file_size_change<br /><br /> lock_timeout_greater_than_0<br /><br /> lock_timeout|  
  
 **XEvent の追加変更**  
  
 **resource_monitor_ring_buffer_record**:  
  
-   削除したフィールド: single_pages_kb、multiple_pages_kb  
  
-   追加したフィールド: target_kb、pages_kb  
  
 **memory_node_oom_ring_buffer_recorded**:  
  
-   削除したフィールド: single_pages_kb、multiple_pages_kb  
  
-   追加したフィールド: target_kb、pages_kb  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 データベース エンジンの非推奨の機能](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
