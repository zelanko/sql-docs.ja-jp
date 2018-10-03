---
title: マネージ バックアップ (SQL Server Management Studio) の構成 |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 0403d34b48b74d0517aaf3cb31ea520dbc436f89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165602"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>マネージド バックアップの構成 (SQL Server Management Studio)
  **マネージ バックアップ**ダイアログ ボックスでは、構成できます。[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]インスタンスの既定値。 このトピックでは、このダイアログ ボックスを使用して構成する方法を説明します。[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]インスタンスとその際に考慮する必要がありますオプションの既定の設定。 ときに[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が構成されているインスタンスの場合は、設定はその後作成された新しいデータベースに適用されます。  
  
 構成する場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]特定のデータベースを参照してください。[を構成する SQL Server Managed Backup to Windows Azure のデータベースの有効化と](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)します。  
 
> [!NOTE] 
> プロキシ サーバーでは SQL Server Managed Backup はサポートされていません。 
  
## <a name="task-list"></a>タスク一覧  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 関数を使用して SQL Server Management Studio でのバックアップのインターフェイスを管理します。  
 このリリースを使用してインスタンス レベルの既定の設定を構成することができますのみ、**管理バックアップ**インターフェイス。 構成することはできません[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]データベースでは、一時停止または再開[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]操作、または電子メール通知を設定します。 現在サポートされていない操作を実行する方法について、**マネージ バックアップ**インターフェイスは、「 [SQL Server Managed Backup to Windows Azure - 保有期間とストレージ設定](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 **マネージ バックアップ ノードのビューは、SQL Server Management Studio:** を表示する**マネージ バックアップ**ノード**オブジェクト エクスプ ローラー**、システム管理者であるか、次のアクセス許可する必要があります具体的には、自分のユーザー アカウントに付与されます。  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` `smart_admin.fn_is_master_switch_on`します。  
  
-   `SELECT` `smart_admin.fn_backup_instance_config`します。  
  
 **マネージ バックアップを構成する**を構成する[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]SQL Server Management studio でシステム管理者であるか次のアクセス許可する必要があります。  
  
 メンバーシップ`db_backupoperator`データベース ロール、`ALTER ANY CREDENTIAL`アクセス許可、および`EXECUTE`に対する`sp_delete_backuphistory`ストアド プロシージャ。  
  
 `SELECT` アクセス許可、`smart_admin.fn_get_current_xevent_settings`関数。  
  
 `EXECUTE` アクセス許可、`smart_admin.sp_get_backup_diagnostics`ストアド プロシージャ。 さらに、`VIEW SERVER STATE` 権限も必要です (この権限を必要とする他のシステム オブジェクトを内部的に呼び出すため)。  
  
 `EXECUTE` アクセス許可`smart_admin.sp_set_instance_backup`、および`smart_admin.sp_backup_master_switch`します。  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>構成[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]SQL Server Management Studio を使用します。  
 **オブジェクト エクスプ ローラー**、展開、**管理**ノード、および右クリック**マネージ バックアップ**します。 **[構成]** を選択します。 **[マネージド バックアップ]** ダイアログ ボックスが開きます。  
  
 確認**マネージ バックアップを有効にする**オプションし、構成値を指定します。  
  
 **ファイル保有**期間を日数で指定し、1 ~ 30 にする必要があります。  
  
 **SQL 資格情報**を選択しますが、ストレージ アカウントと一致する必要があります。 現在の認証情報を格納する SQL 資格情報がないをクリックして 1 つを作成できます**作成**です。 Transact-SQL の CREATE CREDENTIAL ステートメントを使用して資格情報を作成することもできます。その場合、Identity パラメーターにはストレージ アカウント名を、SECRET パラメーターにはアクセス キーを指定します。 詳細については、次を参照してください。[資格情報を作成](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential)です。  
  
 指定、**ストレージ URL** Windows Azure ストレージ アカウント、ストレージ アカウントの認証情報と、バックアップ ファイルの保有期間を格納する SQL 資格情報。  
  
 ストレージ URL の形式: https://\<StorageAccount >.blob.core.windows.net/  
  
 インスタンス レベルの暗号化の設定を設定するには、確認**バックアップを暗号化**オプション、およびアルゴリズムと証明書または暗号化に使用する非対称キーを指定します。  この設定がインスタンス レベルで設定され、この構成の適用後、新しく作成されたすべてのデータベースに使用されます。  
  
> [!WARNING]  
>  構成しなくても、暗号化オプションを指定するこのダイアログ ボックスを使用することはできません[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]します。 これらの暗号化オプションはのみに適用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]操作。 その他のバックアップの暗号化を使用する、次を参照してください。[バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)します。  
  
### <a name="considerations"></a>考慮事項  
 構成する場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]インスタンス レベルでは、設定はその後作成された新しいデータベースに適用されます。  ただし既存のデータベースがこれらの設定を自動的に継承することはありません。 構成する[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]に既存のデータベース、具体的には各データベースを構成する必要があります。 詳細については、次を参照してください。[を構成する SQL Server Managed Backup to Windows Azure のデータベースの有効化と](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)します。  
  
 場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用して一時停止されましたが、 `smart_admin.sp_backup_master_switch`、警告メッセージが表示されます「マネージ バックアップが無効になっているし、現在の構成は反映されません」。 構成の完了時に表示されます。 使用して、`smart_admin.sp_backup_master_switch`格納され、設定、 @new_state= 1。 これは再開[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]サービスおよび構成設定は、有効になります。 ストアド プロシージャの詳細については、次を参照してください。 [smart_admin.sp_ backup_master_switch &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)します。  
  
## <a name="see-also"></a>参照  
 [Windows Azure への SQL Server マネージ バックアップ: 相互運用性と共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
