---
title: マネージバックアップの構成 (SQL Server Management Studio) |Microsoft Docs
description: '[マネージバックアップ] ダイアログボックスを使用すると、SQL Server Managed Backup to Azure default 設定を構成できます。 考慮する必要があるオプションについて説明します。'
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e952ef1102ac67bd0ed9f72d0c201d54b320b5ca
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935993"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>マネージド バックアップの構成 (SQL Server Management Studio)
  [**マネージバックアップ**] ダイアログボックスでは、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] インスタンスの既定値を構成できます。 このトピックでは、インスタンスに使用する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の既定の設定をこのダイアログで構成する方法とその際に考慮する必要のあるオプションについて説明します。 インスタンスに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成すると、それ以降に作成された新しいデータベースにその設定が適用されます。  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]特定のデータベースに対してを構成する場合は、「[データベースの Azure への SQL Server マネージバックアップの有効化と構成](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)」を参照してください。  
 
> [!NOTE] 
> プロキシ サーバーでは SQL Server Managed Backup はサポートされていません。 
  
## <a name="task-list"></a>タスク一覧  
  
## <a name="ss_smartbackup-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>SQL Server Management Studio のマネージド バックアップ インターフェイスを使用する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の機能  
 このリリースでは、**管理バックアップ**インターフェイスを使用してインスタンスレベルの既定の設定のみを構成できます。 データベースに対する [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成することはできず、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 操作を一時停止 (または再開) したり、電子メール通知を設定したりすることもできません。 **マネージバックアップ**インターフェイスで現在サポートされていない操作を実行する方法の詳細については、「 [Azure へのマネージバックアップの SQL Server](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 **マネージバックアップノードの表示は SQL Server Management Studio:****オブジェクトエクスプローラー**で**管理対象のバックアップ**ノードを表示するには、システム管理者であるか、ユーザーアカウントに次のアクセス許可が明示的に付与されている必要があります。  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` に対する `smart_admin.fn_is_master_switch_on`。  
  
-   `SELECT` に対する `smart_admin.fn_backup_instance_config`。  
  
 **マネージバックアップを構成するには:** SQL Server Management Studio でを構成するに [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は、システム管理者であるか、次のアクセス許可を持っている必要があります。  
  
 `db_backupoperator` データベース ロールのメンバーシップ、`ALTER ANY CREDENTIAL` 権限、`sp_delete_backuphistory` ストアド プロシージャに対する `EXECUTE` 権限。  
  
 `smart_admin.fn_get_current_xevent_settings` 関数に対する `SELECT` 権限。  
  
 `EXECUTE`ストアドプロシージャに対する権限 `smart_admin.sp_get_backup_diagnostics` 。 さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。  
  
 `smart_admin.sp_set_instance_backup` および `smart_admin.sp_backup_master_switch` に対する `EXECUTE` 権限。  
  
## <a name="configure-ss_smartbackup-using-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]SQL Server Management Studio を使用して構成する  
 **オブジェクトエクスプローラー**で、[**管理**] ノードを展開し、[**マネージバックアップ**] を右クリックします。 **[構成]** をクリックします。 **[マネージド バックアップ]** ダイアログ ボックスが開きます。  
  
 [**マネージバックアップを有効にする**] オプションをオンにして、構成値を指定します。  
  
 **ファイルの保有**期間は日数で指定し、1 ~ 30 の範囲で指定する必要があります。  
  
 選択する**SQL 資格情報**は、ストレージアカウントと一致している必要があります。 現在、認証情報を格納する SQL 資格情報がない場合は、[**作成**] をクリックして作成できます。 Transact-SQL の CREATE CREDENTIAL ステートメントを使用して資格情報を作成することもできます。その場合、Identity パラメーターにはストレージ アカウント名を、SECRET パラメーターにはアクセス キーを指定します。 詳細については、「[資格情報を作成する](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential)」を参照してください。  
  
 Azure ストレージアカウントの**ストレージ URL** 、ストレージアカウントの認証情報を格納する SQL 資格情報、およびバックアップファイルの保有期間を指定します。  
  
 ストレージ URL の形式は次のとおりです: https:// \<StorageAccount> . blob.core.windows.net/  
  
 インスタンスレベルで暗号化設定を設定するには、[**バックアップの暗号化**] オプションをオンにし、暗号化に使用するアルゴリズムと証明書または非対称キーを指定します。  この設定がインスタンス レベルで設定され、この構成の適用後、新しく作成されたすべてのデータベースに使用されます。  
  
> [!WARNING]  
>  このダイアログで、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成せずに暗号化のオプションを指定することはできません。 ここで指定した暗号化のオプションは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] の操作にのみ適用されます。 他のバックアップ手順で暗号化を使用するには、「[バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)」を参照してください。  
  
### <a name="considerations"></a>考慮事項  
 インスタンス レベルで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成した場合、それ以降に作成された新しいデータベースにその設定が適用されます。  ただし既存のデータベースがこれらの設定を自動的に継承することはありません。 既存のデータベースに対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] を構成するには、各データベースを個別に構成する必要があります。 詳細については、「[データベースの Azure への SQL Server マネージバックアップの有効化と構成](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)」を参照してください。  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]がを使用して一時停止されている場合 `smart_admin.sp_backup_master_switch` 、"管理されたバックアップは無効になり、現在の構成は有効になりません..." という警告メッセージが表示されます。構成を完了しようとしたとき。 格納されているを使用 `smart_admin.sp_backup_master_switch` し、= 1 を設定し @new_state ます。 これで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] サービスが再開され、構成設定が有効になります。 ストアドプロシージャの詳細については、「 [smart_admin sp_ backup_master_switch &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Azure への SQL Server マネージド バックアップ:相互運用性と共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
