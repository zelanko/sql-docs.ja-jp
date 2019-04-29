---
title: Windows Azure への SQL Server マネージド バックアップ:相互運用性と共存 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 78fb78ed-653f-45fe-a02a-a66519bfee1b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d4d883d54a1ad933d4e248f292d9b6a222915a00
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842909"
---
# <a name="sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence"></a>Windows Azure への SQL Server マネージド バックアップ:相互運用性と共存
  このトピックでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] のいくつかの機能との [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の相互運用性および共存について説明します。 使用できる機能には、次のようなものがあります。AlwaysOn 可用性グループ、データベース ミラーリング、バックアップ メンテナンス プラン、ログ配布、アドホック バックアップ、データベースのデタッチ、および Drop Database。  
  
### <a name="alwayson-availability-groups"></a>AlwaysOn 可用性グループ  
 Windows のサポートされている Azure のみのソリューションとして構成されている AlwaysOn 可用性グループ[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]します。 内部設置型のみまたはハイブリッドの AlwaysOn 可用性グループの構成はサポートされていません。 他の考慮事項と詳細については、次を参照してください[可用性グループの SQL Server Managed Backup to Windows Azure の設定。](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)  
  
### <a name="database-mirroring"></a>データベース ミラーリング  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、プリンシパル データベースでのみサポートされます。 プリンシパルとミラーの両方が [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用するように構成されている場合、ミラーリングされたデータベースはスキップされ、バックアップされません。 ただしフェールオーバーが発生した場合、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、ミラーが役割の交代を完了してオンラインになった後に、バックアップ プロセスを開始します。 この場合、バックアップは新しいコンテナーに格納されます。 ミラーが [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用するように構成されていない場合は、フェールオーバー時にはバックアップがまったく作成されません。 フェールオーバー時にもバックアップが継続されるように、プリンシパルとミラーの両方に対して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を構成することをお勧めします。  
  
> [!TIP]  
>  ミラー化されたデータベースを [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の既定の設定でインスタンス上に作成する場合、ミラー化されたデータベースに適用されないように [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] インスタンスの既定値を無効にして、プリンシパルとミラーを構成した後でインスタンスの既定値を有効にする方が望ましいことがあります。  
  
### <a name="maintenance-plan"></a>メンテナンス プラン  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が有効になっている場合、データベースのバックアップ作成にメンテナンス プランを使用することはできません。 メンテナンス プランを使用すると、ログ チェーンが中断されます。また、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、復元中にデータベースの保障された復旧をサポートできなくなる可能性があります。 これは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]がインスタンス レベルで有効になっている場合にも適用されます。  
  
> [!TIP]  
>  コピーのみのバックアップを指定したメンテナンス プランは、同じデータベースまたはインスタンスで [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を構成することによってサポートされます。  
  
### <a name="log-shipping"></a>ログ配布  
 同じデータベースに対してログ配布と [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を同時に構成することはできません。 同時に構成すると、いずれかの機能を使用したデータベースの復元に影響します。  
  
### <a name="ad-hoc-backups-using-transact-sql-and-sql-server-management-studio"></a>Transact-SQL と SQL Server Management Studio を使用したアドホック バックアップ  
 Transact-SQL または SQL Server Management Studio を使用して [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の外部で作成したアドホック バックアップ (1 回限りのバックアップ) は、バックアップの種類と使用される記憶域メディアに応じて、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] プロセスに影響する場合があります。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]で使用されているものとは別の Windows Azure ストレージ アカウントまたは Windows Azure BLOB ストレージ サービス以外のバックアップ先へのログ バックアップは、ログ チェーンが中断される原因となります。 使用することをお勧め、 [smart_admin.sp_backup_on_demand &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)ストアド プロシージャがデータベースでバックアップを開始する[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を有効にします。 このストアド プロシージャを使用して、データベースの完全バックアップまたはログ バックアップのどちらかを開始できます。  
  
### <a name="drop-database-and-detach-database"></a>データベースの削除とデータベースのデタッチ  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が有効になっているデータベースをデタッチまたは削除すると、さらにバックアップすることはできなくなりますが、以前のバックアップは、保有期間が経過するまでストレージ内に保持され、保有期間が経過した時点で削除されます。  
  
### <a name="changes-to-recovery-model"></a>復旧モデルへの変更  
  
-   データベースの復旧モデルを変更するかどうか**単純な**に**完全**または**一括ログ**を構成するオプションがある[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]データベース。 これは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の観点から、新しいデータベースと見なされます。  
  
-   データベースの復旧モデルを変更するかどうかは**完全**または**一括ログ**に**単純**を持つ[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]有効になっている、バックアップ操作はしなくなります。スケジュールされています。 保有期間設定はアクティブのままであるため、保有期間が経過するまでバックアップ ファイルはストレージ アカウントに残ります。 バックアップを保持する必要がある場合は、別のストレージ アカウントまたは内部設置型の場所にファイルをダウンロードすることをお勧めします。 構成設定が保持される、復旧モデルがバックアップ設定されている場合、再利用できる**完全**または**一括ログ**もう一度です。  
  
### <a name="log-backups-using-other-backup-tools-or-custom-scripts"></a>他のバックアップ ツールまたはカスタム スクリプトを使用したログ バックアップ  
 2 つのバックアップが同じデータベースでログ バックアップを実行するように構成されていると、バックアップ ログ チェーンが中断されます。 チェーンの中断が検出されると、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は完全バックアップをスケジュールしてバックアップ チェーンの中断を修復しようとしますが、これは中断が定期的に発生し、競合する 2 つのツールによってログ バックアップが実行されるという状態が続くことを意味します。 また、一方のツールがバックアップの完全なセットを順序どおりに保持することは期待できないため、データベースの回復性に影響する可能性があります。 これは、ログ バックアップを実行する 2 つの機能またはツールに当てはまりますが、次に示す具体的な例を強調する際に役立ちます。 また、これは、このトピックの以前のセクションで説明したメンテナンス プランまたはログ配布の構成に関する問題の根拠でもあります。  
  
 **Data Protection Manager (DPM) ベースのバックアップ。** Microsoft Data Protection Manager を使用する完全と増分バックアップします。 増分バックアップは、トランザクション ログ バックアップの作成後にログの切り捨てを実行するログ バックアップです。 そのため、同じデータベースで DPM と [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の両方を構成することはできません。  
  
 **サード パーティ製ツールまたはスクリプト:** 任意のサード パーティ製ツールまたは原因となるログの切り捨てと互換性がないログ バックアップを実行するスクリプト[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はサポートされていません。  
  
 あれば[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]データベース インスタンスの場合に有効になっており、使用するか、アドホック バックアップを実行する、 [smart_admin.sp_backup_on_demand &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)には、前述の説明に従って、ストアド プロシージャセクション。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]以外に、スケジュールや定期的なバックアップも必要な場合は、[バックアップのみコピーする] を使用できます。  詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。  
  
  
