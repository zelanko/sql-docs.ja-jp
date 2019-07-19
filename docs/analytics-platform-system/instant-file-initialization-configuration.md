---
title: Analytics Platform System を構成するには、ファイルの瞬時初期化の |Microsoft Docs
description: Analytics Platform System では、ファイルの瞬時初期化を構成します。 ファイルの瞬時初期化より迅速に実行するデータ ファイルの操作を許可する SQL Server 機能です。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 27f716b5fc3668b78fd7e5728dc4a2cd640c7940
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960732"
---
# <a name="instant-file-initialization-configuration"></a>ファイルの瞬時初期化の構成
ファイルの瞬時初期化より迅速に実行するデータ ファイルの操作を許可する SQL Server 機能です。 チェック ボックスをファイルの瞬時初期化を有効にすると、SQL Server PDW のパフォーマンスが向上します。 ただし、ビジネスのセキュリティ リスクをもたらすこの場合、オフのままにします。  
  
> [!IMPORTANT]  
> ファイルの瞬時初期化を有効にすると、SQL Server ではゼロの削除済みのビットは上書きされません。  この動作は、承認されていないユーザーに削除されたデータにアクセスした場合、セキュリティの脆弱性を作成可能性があります。 ただし、SQL Server PDW は、SQL Server データベースとバックアップ ファイルが SQL Server のインスタンスに常に接続されていることを確認してこのリスクを軽減SQL Server サービス アカウントのみおよびローカルの管理者は、SQL Server PDW で削除されたデータにアクセスできます。  
  
ファイルの瞬時初期化は、TDE が有効になっている場合は使用できません。  
  
## <a name="add-permission-for-the-backup-account"></a>バックアップ アカウントのアクセス許可を追加します。  
バックアップ プロセスでは、バックアップ記憶域の場所にアクセスできるネットワーク資格情報 (Windows ユーザー アカウント) が必要です。 使用してアカウントを使用する PDW の承認、 [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)プロシージャ。 参照してください[BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)バックアップ プロセス全体の。 ファイルの瞬時初期化を使用するバックアップ アカウントに付与する必要があります、`Perform volume maintenance tasks`権限。  
  
1.  Backup server を開き、**ローカル セキュリティ ポリシー**アプリケーション (`secpol.msc`)。  
  
2.  左側のペインで **[ローカル ポリシー]** を展開し、 **[ユーザー権利の割り当て]** をクリックします。  
  
3.  右側のペインで、 **[ボリュームの保守タスクを実行]** をダブルクリックします。  
  
4.  **[ユーザーまたはグループの追加]** をクリックし、バックアップに使用される任意のユーザー アカウントを追加します。  
  
5.  **[適用]** をクリックし、 **[ローカル セキュリティ ポリシー]** ダイアログ ボックスをすべて閉じます。  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>ファイルの瞬時初期化を有効または無効にする  
  
1.  Configuration Manager を起動します。 詳細については、次を参照してください。 [Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)します。  
  
2.  Configuration Manager の左側のウィンドウで次のようにクリックします。**ファイルの瞬時初期化**します。  
  
3.  ファイルの瞬時初期化を有効にするには、ボックスを横にオン**Enable Instant File Initialization すべてのノードで**します。 ファイルの瞬時初期化を無効にするには、ボックスを横にオフ**Enable Instant File Initialization すべてのノードで**します。  
  
    > [!WARNING]  
    > ファイルの瞬時初期化を無効にすると機能の前に説明したセキュリティの考慮事項もファイルの瞬時初期化が有効になっている削除されたファイルに適用されます。  
  
4.  **[適用]** をクリックします。 変更は、アプライアンスのサービスが再起動したときに、SQL Server PDW に対する SQL Server のインスタンスを通じて伝達されます。 アプライアンスのサービスを今すぐ再起動するには、次を参照してください。 [PDW のサービス状態&#40;Analytics Platform System&#41;](pdw-services-status.md)します。  
  
5.  上記の手順を繰り返す場合**バックアップ アカウントのアクセス許可を追加**を削除する、**ボリュームの保守タスクを実行**権限。  
  
![DWConfig アプライアンス PDW のインスタント ファイル初期化](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
ファイルの瞬時初期化の詳細については、次を参照してください。[ファイルの瞬時初期化](https://technet.microsoft.com/library/ms175935(v=SQL.105).aspx)します。  
  
