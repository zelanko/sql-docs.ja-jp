---
title: Enable および Disable AlwaysOn 可用性グループ (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cafc562581a5f34bf9b59b1ff7cde1c679abd726
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228644"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a>AlwaysOn 可用性グループの有効化と無効化 (SQL Server)
  サーバー インスタンスで可用性グループを使用するには、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を有効にする必要があります。 可用性グループを作成したり構成したりするためには、少なくとも 1 つの可用性グループの可用性レプリカがホストされる [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の各インスタンスで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能が有効になっている必要があります。  
  
> [!IMPORTANT]  
>  WSFC クラスターを削除してから再作成した場合は、元の WSFC クラスター上の可用性レプリカをホストしていた [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の各インスタンスについて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能を無効にしてから再度有効にする必要があります。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **操作方法:**  
  
    -   [かどうかの AlwaysOn 可用性グループが有効になっているかを決定します。](#IsEnabled)  
  
    -   [AlwaysOn 可用性グループを有効にします。](#EnableAOAG)  
  
    -   [AlwaysOn 可用性グループを無効にします。](#DisableAOAG)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Prerequisites"></a> AlwaysOn 可用性グループを有効にするための前提条件  
  
-   このサーバー インスタンスは、Windows Server フェールオーバー クラスタリング (WSFC) ノードに存在している必要があります。  
  
-   [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートする SQL Server エディションが実行されている必要があります。 詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。  
  
-   一度に 1 つのサーバー インスタンスでのみ AlwaysOn 可用性グループを有効にします。 AlwaysOn 可用性グループを有効にした後まで待って、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]別のサーバー インスタンスを続行する前に、サービスが再起動します。  
  
 追加の前提条件を作成すると、可用性グループの構成については、次を参照してください。[前提条件、制限事項、および AlwaysOn 可用性グループの推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)します。  
  
###  <a name="Security"></a> セキュリティ  
 インスタンスで AlwaysOn 可用性グループが有効になっている[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、サーバー インスタンスが WSFC クラスターに対するフル コントロール。  
  
####  <a name="Permissions"></a> Permissions  
 ローカル コンピューターの **Administrator** グループのメンバーシップおよび WSFC クラスターに対するフル コントロール権限が必要です。 PowerShell を使用して AlwaysOn を有効にする場合は、 **[管理者として実行]** オプションを使用してコマンド プロンプト ウィンドウを開いてください。  
  
 Active Directory の Create Objects 権限と Manage Objects 権限が必要です。  
  
##  <a name="IsEnabled"></a> かどうかの AlwaysOn 可用性グループが有効になっているかを決定します。  
  
-   [SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="SSMS1Procedure"></a> SQL Server Management Studio の使用  
 **AlwaysOn 可用性グループが有効になっているかどうかを判断するには**  
  
1.  オブジェクト エクスプローラーでサーバー インスタンスを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[サーバーのプロパティ]** ダイアログ ボックスの **[全般]** ページをクリックします。 **[HADR が有効]** プロパティに、次のいずれかの値が表示されます。  
  
    -   **True**(AlwaysOn 可用性グループが有効である場合)  
  
    -   **False**(AlwaysOn 可用性グループが無効である場合)  
  
###  <a name="Tsql1Procedure"></a> Transact-SQL の使用  
 **AlwaysOn 可用性グループが有効になっているかどうかを判断するには**  
  
1.  次の [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) ステートメントを使用します。  
  
    ```  
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     `IsHadrEnabled` サーバー プロパティの設定は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに対して AlwaysOn 可用性グループが有効であるかどうかを示します。  
  
    -   場合`IsHadrEnabled`= 1、AlwaysOn 可用性グループを有効にします。  
  
    -   場合`IsHadrEnabled`= 0、AlwaysOn 可用性グループが無効になっています。  
  
    > [!NOTE]  
    >  詳細については、`IsHadrEnabled`サーバーのプロパティを参照してください[SERVERPROPERTY &#40;TRANSACT-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)します。  
  
###  <a name="PowerShell1Procedure"></a> PowerShell の使用  
 **AlwaysOn 可用性グループが有効になっているかどうかを判断するには**  
  
1.  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]が有効であるかどうかを確認するサーバー インスタンスを既定の操作対象に設定 (`cd`) します。  
  
2.  PowerShell コマンド `Get-Item` を入力します。  
  
    ```  
    PS SQLSERVER:\SQL\NODE1\DEFAULT> get-item . | select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示する、`Get-Help`コマンドレット、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="EnableAOAG"></a> [AlwaysOn 可用性グループを有効にする]  
 **AlwaysOn を有効にするを使用します。**  
  
-   [SQL Server 構成マネージャー](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="SQLCM2Procedure"></a> SQL Server 構成マネージャーの使用  
 **AlwaysOn 可用性グループを有効にするには**  
  
1.  ホストする Windows Server フェールオーバー クラスタ リング (WSFC) ノードに接続する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスの AlwaysOn 可用性グループを有効にします。  
  
2.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
3.  **SQL Server 構成マネージャー**、 をクリックして**SQL Server サービス**、SQL サーバーを右クリックして (**<*`instance name`*>)** ここで、 **< *`instance name`* >** AlwaysOn 可用性グループを有効にするローカル サーバー インスタンスの名前を指定し、クリックして**プロパティ。**  
  
4.  **[AlwaysOn 高可用性]** タブを選択します。  
  
5.  **[Windows フェールオーバー クラスター名]** フィールドに、ローカル フェールオーバー クラスターの名前が表示されていることを確認します。 このフィールドが空白の場合、このサーバー インスタンスは現在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートしていません。 ローカル コンピューターがクラスター ノードではないか、WSFC クラスターがシャットダウンされています。または、このエディションの [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] では [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]がサポートされません。  
  
6.  **[AlwaysOn 可用性グループを有効にする]** チェック ボックスをオンにし、 **[OK]** をクリックします。  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーによって変更内容が保存されます。 その後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを手動で再起動する必要があります。 業務上の要件に合った時間帯を選んで再起動することができます。 ときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスが再起動、AlwaysOn が有効にする、および`IsHadrEnabled`サーバー プロパティを 1 に設定されます。  
  
###  <a name="PScmd2Procedure"></a> SQL Server PowerShell の使用  
 **AlwaysOn を有効にするには**  
  
1.  ディレクトリ変更コマンド (`cd`) を使用して、AlwaysOn 可用性グループを有効にするサーバー インスタンスに移動します。  
  
2.  使用して、 `Enable-SqlAlwaysOn` AlwaysOn 可用性グループを有効にするコマンドレットです。  
  
     コマンドレットの構文を表示する、`Get-Help`コマンドレット、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
    > [!NOTE]  
    >  制御する方法についてはかどうか、`Enable-SqlAlwaysOn`コマンドレットでは再起動、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスを参照してください[コマンドレットは、SQL Server サービス再起動するとしますか?](#WhenCmdletRestartsSQL)、このトピックで後述します。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="ExmplEnable-SqlHadrServic"></a> 例: Enable-SqlAlwaysOn  
 次の PowerShell コマンドは、SQL Server のインスタンス ( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Computer*Instance*\\ *) の*を有効にします。  
  
```  
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="DisableAOAG"></a> AlwaysOn 可用性グループを無効にします。  
  
-   **AlwaysOn を無効にする前に。**  
  
     [推奨事項](#Recommendations)  
  
-   **AlwaysOn を無効にするを使用します。**  
  
    -   [SQL Server 構成マネージャー](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **補足情報:**  [AlwaysOn を無効にした後](#FollowUp)  
  
> [!IMPORTANT]  
>  AlwaysOn を無効にできるサーバー インスタンスは一度に 1 つだけです。 AlwaysOn 可用性グループを無効にした後は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動するまで待ってから、次のサーバー インスタンスを有効にしてください。  
  
###  <a name="Recommendations"></a> 推奨事項  
 サーバー インスタンスで AlwaysOn を無効にする前に、次の操作を行うことをお勧めします。  
  
1.  保持する可用性グループのプライマリ レプリカをサーバー インスタンスがホスト中の場合は、同期されたセカンダリ レプリカに可用性グループを手動でフェールオーバーすることをお勧めします (可能な場合)。 詳細については、「[可用性グループの計画的な手動フェールオーバーの実行 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)」を参照してください。  
  
2.  ローカル セカンダリ レプリカをすべて削除します。 詳細については、「[可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)」を参照してください。  
  
###  <a name="SQLCM3Procedure"></a> SQL Server 構成マネージャーの使用  
 **AlwaysOn を無効にするには**  
  
1.  対象の (AlwaysOn 可用性グループを無効にする) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスがホストされている Windows Server フェールオーバー クラスタリング (WSFC) ノードに接続します。  
  
2.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
3.  **SQL Server 構成マネージャー**、 をクリックして**SQL Server サービス**、SQL サーバーを右クリックして (**<*`instance name`*>)** ここで、 **< *`instance name`* >** AlwaysOn 可用性グループを無効にするローカル サーバー インスタンスの名前を指定し、クリックして**プロパティ**します。  
  
4.  **[AlwaysOn 高可用性]** タブで、 **[AlwaysOn 可用性グループを有効にする]** チェック ボックスをオフにし、 **[OK]** をクリックします。  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーによって変更内容が保存され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスが再起動すると、AlwaysOn が無効になり、`IsHadrEnabled` サーバー プロパティは、AlwaysOn 可用性グループが無効であることを示す 0 に設定されます。  
  
5.  このトピックの「 [補足情報: AlwaysOn を無効にした後](#FollowUp)」を読むことをお勧めします。  
  
###  <a name="PScmd3Procedure"></a> SQL Server PowerShell の使用  
 **AlwaysOn を無効にするには**  
  
1.  ディレクトリ変更コマンド (`cd`) を使用して、AlwaysOn 可用性グループを無効にするサーバー インスタンスに移動します。  
  
2.  使用して、 `Disable-SqlAlwaysOn` AlwaysOn 可用性グループを有効にするコマンドレットです。  
  
     たとえば、次のコマンドは SQL Server のインスタンスで AlwaysOn 可用性グループを無効にします (*コンピューター*\\*インスタンス*)。  このコマンドの場合、インスタンスを再起動する必要があり、再起動するかどうかを確認するメッセージが表示されます。  
  
    ```  
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  制御する方法についてはかどうか、`Disable-SqlAlwaysOn`コマンドレットでは再起動、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスを参照してください[コマンドレットは、SQL Server サービス再起動するとしますか?](#WhenCmdletRestartsSQL)、このトピックで後述します。  
  
     コマンドレットの構文を表示する、`Get-Help`コマンドレット、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="FollowUp"></a> 補足情報: AlwaysOn を無効にした後  
 AlwaysOn 可用性グループのインスタンスを無効にした後[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]再起動する必要があります。 サーバー インスタンスは、SQL 構成マネージャーによって自動的に再起動されます。 ただし、`Disable-SqlAlwaysOn` コマンドレットを使用した場合は、サーバー インスタンスを手動で再起動する必要があります。 詳細については、「 [sqlservr Application](../../../tools/sqlservr-application.md)」を参照してください。  
  
 再起動後のサーバー インスタンスに該当する状況を以下に示します。  
  
-   SQL Server の起動時に可用性データベースは開始されず、アクセス不能となります。  
  
-   のみでサポートされる AlwaysOn[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントが[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)します。 CREATE AVAILABILITY GROUP と ALTER AVAILABILITY GROUP、および ALTER DATABASE の SET HADR オプションはサポートされません。  
  
-   AlwaysOn 可用性グループを無効にしても、WSFC 内の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の構成データと [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のメタデータにその影響が及ぶことはありません。  
  
 1 つまたは複数の可用性グループの可用性レプリカをホストするすべてのサーバー インスタンスで AlwaysOn 可用性グループを永続的に無効にする場合は、次の手順を完了することをお勧めします。  
  
1.  AlwaysOn を無効にする前にローカル可用性レプリカを削除しなかった場合は、サーバー インスタンスが可用性レプリカをホストしている可用性グループを削除します。 可用性グループの削除については、「[可用性グループの削除 &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)」を参照してください。  
  
2.  残されたメタデータを除去するには、元の WSFC クラスターの一部であるサーバー インスタンスから影響を受ける可用性グループを削除します。  
  
3.  プライマリ データベースには引き続きすべての接続からアクセスできますが、プライマリ データベースとセカンダリ データベース間のデータの同期は中止されます。  
  
4.  セカンダリ データベースは、RESTORING 状態に入ります。 これらは削除するか、RESTORE WITH RECOVERY を使用して復元できます。 ただし、復元されたデータベースは、それ以降、可用性グループのデータの同期対象とはなりません。  
  
##  <a name="WhenCmdletRestartsSQL"></a> SQL Server サービスがコマンドレットによって再起動される条件  
 現在実行中のサーバー インスタンスで、`Enable-SqlAlwaysOn` または `Disable-SqlAlwaysOn` を使用して現在の AlwaysOn 設定を変更すると、SQL Server サービスが再起動されます。 再起動の動作は次の条件によって異なります。  
  
|-NoServiceRestart パラメーターの指定|-Force パラメーターの指定|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの再起動|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|いいえ|いいえ|既定では再起動されます。 ただし、次のプロンプトが表示されます。<br /><br /> **このアクションを完了するには、サーバー インスタンス '<instance_name>' の SQL Server サービスを再起動する必要があります。続行しますか?**<br /><br /> **[Y] はい  [N] いいえ  [S] 中断  [?] ヘルプ (既定値は "Y"):**<br /><br /> **N** または **S**を指定した場合、サービスは再起動されません。|  
|いいえ|はい|サービスは再起動されます。|  
|はい|いいえ|サービスは再起動されません。|  
|はい|はい|サービスは再起動されません。|  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)  
  
  
