---
title: AlwaysOn パブリケーションデータベースのメンテナンス (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a862c5c9cea1087f54a4dbff13b6c39eb5e39385
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62791991"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a>AlwaysOn パブリケーション データベースのメンテナンス (SQL Server)
  このトピックでは、AlwaysOn 可用性グループを使用するときのパブリケーション データベースのメンテナンスについての特別な考慮事項について説明します。  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a>可用性グループでのパブリッシュされたデータベースのメンテナンス  
 AlwaysOn パブリケーション データベースのメンテナンスは、通常のパブリケーション データベースのメンテナンスと基本的に同じです。ただし、次の点を考慮する必要があります。  
  
-   管理は、プライマリ レプリカ ホストで行う必要があります。 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]では、プライマリ レプリカ ホストと読み取り可能なセカンダリ レプリカの **[ローカル パブリケーション]** フォルダーにパブリケーションが表示されます。 フェールオーバー後、プライマリに昇格したセカンダリが読み取り不可である場合は、変更を反映させるために [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] を手動で更新する必要がある場合があります。  
  
-   レプリケーション モニターは、常に元のパブリッシャーの下でパブリケーション情報を表示します。 ただし、元のパブリッシャーをサーバーとして追加することで、この情報を任意のレプリカからレプリケーション モニターで表示することができます。  
  
-   ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO) を使用して現在のプライマリでレプリケーションを管理する場合、パブリッシャー名を指定する際には、データベースのレプリケーションを有効にしたインスタンス (元のパブリッシャー) の名前を指定する必要があります。 適切な名前を決定するには、`PUBLISHINGSERVERNAME` 関数を使用します。 パブリッシング データベースを可用性グループに参加させると、セカンダリ データベース レプリカに格納されているレプリケーション メタデータは、プライマリにあるレプリケーション メタデータと同一になります。 その結果、プライマリでレプリケーションが有効なパブリケーション データベースでは、セカンダリのシステム テーブルに格納されるパブリッシャー インスタンス名は、セカンダリではなくプライマリの名前になります。 これにより、パブリケーション データベースがセカンダリにフェールオーバーした場合に、レプリケーションの構成およびメンテナンスに影響が出ます。 たとえば、フェールオーバー後にセカンダリでストアドプロシージャを使用してレプリケーションを構成していて、別のレプリカで有効にされたパブリケーションデータベースに対するプルサブスクリプションが必要な場合、またはの*@publisher* `sp_addpullsubscription`パラメーターとして、現在のパブリッシャーで`sp_addmergepulllsubscription`はなく元のパブリッシャーの名前を指定する必要があります。 ただし、フェールオーバー後にパブリケーション データベースを有効にした場合、システム テーブルに格納されるパブリッシャー インスタンス名は、現在のプライマリ ホストの名前になります。 この場合は、 *@publisher*パラメーターに現在のプライマリレプリカのホスト名を使用します。  
  
    > [!NOTE]  
    >  などの一部のプロシージャ`sp_addpublication`では、 *@publisher*パラメーターはの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスではないパブリッシャーに対してのみサポートされます。このような場合、AlwaysOn に[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]は関係ありません。  
  
-   フェールオーバー後に [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] でサブスクリプションを同期するには、サブスクライバーからプル サブスクリプションを同期し、アクティブなパブリッシャーからプッシュ サブスクリプションを同期します。  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a> 可用性グループからのパブリッシュされたデータベースの削除  
 パブリッシュされたデータベースを可用性グループから削除する場合、またはパブリッシュされたメンバー データベースを含む可用性グループを削除する場合、次の点を考慮します。  
  
-   元のパブリッシャーのパブリケーションデータベースを可用性グループのプライマリレプリカから削除する場合は、パブリッシャー/ `sp_redirect_publisher`データベースペアのリダイレクトを削除*@redirected_publisher*するために、パラメーターの値を指定せずにを実行する必要があります。  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     データベースはプライマリで復旧中の状態のままとなり、復元する必要があります。 データベースを復元すると、レプリケーションは元のパブリッシャーに対して変更なしで動作します。  
  
-   パブリケーション データベースが元のパブリッシャーからレプリカにフェールオーバーし、そのパブリケーション データベースを可用性グループのプライマリ レプリカから削除した場合、ストアド プロシージャ `sp_redirect_publisher` を使用して元のパブリッシャーを新しいパブリッシャーに明示的にリダイレクトします。 データベースは復旧中の状態のままとなり、復元する必要があります。 データベースを復元すると、レプリケーションは可用性グループの下で引き続き機能します。  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     元のパブリッシャーのリモート サーバーは、以降にアクセスできなくなる場合でもディストリビューターから削除しないでください。 ディストリビューターでパブリケーション メタデータ クエリに対応するために、元のパブリッシャーのサーバー メタデータが必要です。  
  
-   可用性グループ全体を削除した場合、メンバーであるレプリケートされたデータベースについての動作は、パブリッシュされたデータベースを可用性グループから削除した場合と同じです。 データベースを復元し、リダイレクトを変更すると、レプリケーションを最後のプライマリから再開できます。 データベースを元のパブリッシャーで復元した場合、リダイレクトを削除する必要があります。 データベースを別のホストで復元した場合、新しいホストに対してリダイレクトを明示的に指定する必要があります。  
  
    > [!NOTE]  
    >  メンバー データベースをパブリッシュした可用性グループを削除した場合、またはパブリッシュされたデータベースを可用性グループから削除した場合、パブリッシュされたデータベースのすべてのコピーは復旧中の状態のままとなります。 それぞれを復元すると、パブリッシュされたデータベースとして表示されます。 1 つのコピーだけをパブリケーション メタデータで保持する必要があります。 パブリッシュされたデータベース コピーのレプリケーションを無効にするには、最初にすべてのサブスクリプションとパブリケーションをデータベースから削除します。  
  
     `sp_dropsubscription` を実行してパブリケーション サブスクリプションを削除します。 ディストリビューターでアクティブなパブリッシングデータベース*@ignore_distributributor*のメタデータを保持するには、パラメーターを1に設定してください。  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     `sp_droppublication` を実行してすべてのパブリケーションを削除します。 ここでも、パラメーター *@ignore_distributor*を1に設定して、アクティブなパブリッシングデータベースのメタデータをディストリビューターで保持します。  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     `sp_replicationdboption` を実行してデータベースのレプリケーションを無効にします。  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     この時点で、パブリッシュされたデータベースのコピーを保持または削除できます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server)](always-on-availability-groups-sql-server.md)  
  
-   [レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [レプリケーション管理に関する FAQ](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [レプリケーションサブスクライバーと AlwaysOn 可用性グループ &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [SQL Server のレプリケーション](../../../relational-databases/replication/sql-server-replication.md)  
  
  
