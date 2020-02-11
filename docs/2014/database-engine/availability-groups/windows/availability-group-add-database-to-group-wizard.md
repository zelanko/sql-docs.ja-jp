---
title: 可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], databases
ms.assetid: 81e5e36d-735d-4731-8017-2654673abb88
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0be8ed6cf2a163b3c195cfb5e4e18440549b501c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62815727"
---
# <a name="use-the-add-database-to-availability-group-wizard-sql-server-management-studio"></a>可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio)
  可用性グループへのデータベースの追加ウィザードを使用して、既存の AlwaysOn 可用性グループに 1 つ以上のデータベースを追加できます。  
  
> [!NOTE]  
>  
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] または PowerShell を使用してデータベースを追加する方法については、「[可用性グループへのデータベースの追加 &#40;SQL Server&#41;](availability-group-add-a-database.md)」を参照してください。  
  
 **このトピックの内容:**  
  
-   **作業を開始する準備:**  
  
     [前提条件と制限](#Prerequisites)  
  
     [セキュリティ](#Security)  
  
-   **データベースを追加するには、**[可用性グループへのデータベース追加ウィザード (SQL Server Management Studio)](#SSMSProcedure)を使用します。    
  
##  <a name="BeforeYouBegin"></a> はじめに  
 可用性グループにデータベースを追加したことがない場合は、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」の「可用性データベース」セクションを参照してください。  
  
###  <a name="Prerequisites"></a>前提条件、制限事項、および推奨事項  
  
-   現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
-   データベースが暗号化されているか、データベース暗号化キー (DEK) を含んでいる場合、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] または [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] を使用してそのデータベースを可用性グループに追加することはできません。 暗号化されたデータベースの暗号化を解除した場合でも、そのログ バックアップには暗号化されたデータが含まれていることがあります。 この場合、データベースに対する初期データの完全同期が失敗する可能性があります。 これは、ログの復元操作にはデータベース暗号化キー (DEK) で使用された証明書が必要なことがあり、その証明書を使用できないことがあるためです。  
  
     **暗号化解除されたデータベースを、ウィザードを使用して可用性グループに追加できるようにするには、次の操作を行います。**  
  
    1.  プライマリ データベースのログ バックアップを作成します。  
  
    2.  プライマリ データベースの完全バックアップを作成します。  
  
    3.  セカンダリ レプリカをホストするサーバー インスタンスでデータベース バックアップを復元します。  
  
    4.  プライマリ データベースから新しいログ バックアップを作成します。  
  
    5.  セカンダリ データベースでこのログ バックアップを復元します。  
  
-   **初期データの完全同期を使用するための前提条件**  
  
    -   可用性グループのレプリカをホストするすべてのサーバー インスタンスで、すべてのデータベース ファイルのパスが同じである必要があります。  
  
    -   セカンダリ レプリカをホストするサーバー インスタンスにプライマリ データベース名が存在することはできません。 これは、新しいセカンダリ データベースがまだ存在しないことを意味します。  
  
    -   ウィザードでバックアップを作成し、バックアップにアクセスするために、ネットワーク共有を指定する必要があります。 プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。 セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。  
  
     ウィザードを使用して初期データの完全同期を実行できない場合は、セカンダリ データベースを手動で準備する必要があります。 これは、ウィザードの実行前でも実行後でもかまいません。 詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)、または PowerShell を使用して、AlwaysOn 可用性グループにセカンダリ データベースを参加させる方法について説明します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a>可用性グループへのデータベース追加ウィザードの使用 (SQL Server Management Studio)  
 **可用性グループへのデータベース追加ウィザードを使用するには**  
  
1.  オブジェクト エクスプローラーで、可用性グループのプライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  
  **[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  データベースを追加する可用性グループを右クリックして、 **[データベースの追加]** を選択します。 可用性グループへのデータベース追加ウィザードが起動します。  
  
4.  
  **[データベースの選択]** ページで 1 つまたは複数のデータベースを選択します。 詳細については、「 [[データベースの選択] ページ &#40;新しい可用性グループウィザード-データベースの追加ウィザード&#41;](select-databases-page-new-availability-group-wizard-and-add-database-wizard.md)」を参照してください。  
  
5.  
  **[最初のデータの同期を選択]** ページで、新しいセカンダリ データベースを作成して可用性グループに参加させる方法を選択します。 次のいずれかのオプションを選択します。  
  
    -   **全角**  
  
         使用している環境が、初期データの同期を自動的に開始するための要件を満たす場合は、このオプションを選択します (詳細については、このトピックの「 [前提条件、制限事項、および推奨事項](#Prerequisites)」をご覧ください)。  
  
         
  **[完全]** を選択すると、可用性グループを作成後、ウィザードはすべてのプライマリ データベースとそのトランザクション ログをネットワーク共有にバックアップし、セカンダリ レプリカをホストするすべてのサーバー インスタンスでそのバックアップを復元しようとします。 その後、ウィザードは、すべてのセカンダリ データベースを可用性グループに参加させます。  
  
         
  **[すべてのレプリカからアクセス可能な共有ネットワーク場所を指定]** フィールドで、レプリカをホストするサーバー インスタンスが読み取り/書き込み権限を持つバックアップ共有を指定します。 ログ バックアップは、ログ バックアップ チェーンの一部になります。 ログ バックアップ ファイルは適切に保存してください。  
  
        > [!IMPORTANT]  
        >  必要なファイル システム権限については、このトピックの「 [前提条件](#Prerequisites)」を参照してください。  
  
    -   **結合のみ**  
  
         セカンダリ レプリカをホストするサーバー インスタンス上のセカンダリ データベースを手動で準備した場合は、このオプションを選択できます。 ウィザードは、既存のセカンダリ データベースを可用性グループに参加させます。  
  
    -   **最初のデータの同期をスキップ**  
  
         プライマリ データベースの独自のデータベースとログ バックアップを使用する場合は、このオプションを選択します。 詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。  
  
     詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;[初期データの同期を選択] ページ](select-initial-data-synchronization-page-always-on-availability-group-wizards.md)」を参照してください。  
  
6.  
  **[既存のセカンダリ レプリカへの接続]** ページで、この可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスがすべて同じユーザー アカウントのサービスとして実行されている場合、 **[すべて接続]** をクリックします。 サーバー インスタンスがサービスとして複数のアカウントで実行されている場合、各サーバー インスタンス名の右側の **[接続]** ボタンをクリックします。  
  
     詳細については、「既存のセカンダリレプリカへの接続」を参照してください。 [&#40;レプリカの追加ウィザードとデータベースの追加ウィザード&#41;](connect-to-existing-secondary-replicas-page.md)です。  
  
7.  
  **[検証]** ページでは、このウィザードで指定した値が、新しい可用性グループ ウィザードの要件を満たしているかどうかが確認されます。 変更が必要な場合は、 **[戻る]** をクリックして前のウィザード ページに戻り、値を変更できます。 その後、**[次へ]** をクリックして **[検証]** ページに戻り、**[検証の再実行]** をクリックします。  
  
     詳細については、「[[検証] ページ &#40;AlwaysOn 可用性グループウィザード&#41;](validation-page-always-on-availability-group-wizards.md)」を参照してください。  
  
8.  
  **[概要]** ページで、新しい可用性グループに対して選択した内容を確認します。 変更が必要な場合は、 **[戻る]** をクリックして、該当するページに戻ります。 必要な変更を加えたら、 **[次へ]** をクリックして、 **[概要]** ページに戻ります。  
  
     詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;概要ページ](summary-page-always-on-availability-group-wizards.md)」を参照してください。  
  
     選択内容に問題がなければ、[スクリプト] をクリックして、ウィザードが実行する手順のスクリプトを作成することもできます。 新しい可用性グループを作成して構成するには、 **[完了]** をクリックします。  
  
9. 可用性グループの作成手順 (エンドポイントの構成、可用性グループの作成、グループへのセカンダリ レプリカの参加) の進行状況が、**[進行状況]** ページに表示されます。  
  
     詳細については、「 [AlwaysOn 可用性グループウィザード&#41;&#40;[進行状況] ページ](progress-page-always-on-availability-group-wizards.md)」を参照してください。  
  
10. 以上の手順が完了すると、 **[結果]** ページに各手順の結果が表示されます。 これらのすべての手順が成功した場合は、新しい可用性グループが完全に構成されます。 手順のいずれかでエラーが発生した場合は、手動で構成を完了する必要があります。 特定のエラーの原因については、 **[結果]** 列の [エラー] リンクをクリックします。  
  
     ウィザードでの作業が完了したら、 **[閉じる]** をクリックして終了します。  
  
     詳細については、「[[結果] ページ &#40;AlwaysOn 可用性グループ ウィザード&#41;](results-page-always-on-availability-group-wizards.md)」を参照してください。  
  
11. すべてのセカンダリ データベースで初期データ同期が自動的に開始されない場合は、まだ参加していないセカンダリ データベースを構成する必要があります。 詳細については、「[AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループのセカンダリデータベースを手動で準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [セカンダリデータベースを可用性グループに参加させる &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [可用性グループにデータベースを追加 &#40;SQL Server&#41;](availability-group-add-a-database.md)   
 [AlwaysOn セカンダリデータベース &#40;SQL Server でのデータ移動の開始&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)   
 [可用性グループにデータベースを追加 &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
  
