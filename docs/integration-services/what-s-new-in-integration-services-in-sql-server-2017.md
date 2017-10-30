---
title: "どのような &#39; SQL Server 2017 における Integration Services の |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: 63aba0f64bc63a3a86e5aa07245375938acdf6e4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/29/2017

---
# <a name="what39s-new-in-integration-services-in-sql-server-2017"></a>どのような &#39; の SQL Server 2017 における Integration Services
このトピックでは、 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]で追加または更新された機能について説明します。

>   [!NOTE]
> SQL Server 2017 には、SQL Server 2016 の機能と SQL Server 2016 更新プログラムで追加された機能も含まれています。 SQL Server 2016 の新しい SSIS 機能については、 [「SQL Server 2016 で Integration Services の新機能」](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)を参照してください。

## <a name="highlights-of-this-release"></a>このリリースの重要なポイント

SQL Server 2017 で Integration Services の最も重要な新機能を次に示します。

-   **スケール アウト**です。複数のワーカーのコンピューター間で SSIS パッケージの実行をより簡単に配布および単一のマスター コンピューターから実行と作業を管理します。 詳細については、次を参照してください。 [Services スケール アウト統合](../integration-services/scale-out/integration-services-ssis-scale-out.md)です。

-   **Linux 上の integration Services**です。 Linux コンピューターでは、SSIS パッケージを実行します。 詳細については、次を参照してください。[抽出、変換、および SSIS での Linux にデータを読み込む](../linux/sql-server-linux-migrate-ssis.md)します。

-   **接続性の向上**です。 OData の更新されたコンポーネントでの Microsoft Dynamics AX Online、Microsoft Dynamics CRM Online OData フィードに接続します。 

## <a name="new-in-azure-data-factory"></a>Azure Data Factory の新機能

Azure Data Factory 2017 年 9 月にバージョン 2 のパブリック プレビュー版、今すぐ、次の処理の操作を行うことができます。
-   Azure SQL データベースで、SSIS カタログ データベース (SSISDB) にパッケージを展開します。
-   Azure SSIS の統合ランタイム、Azure Data Factory バージョン 2 のコンポーネントで Azure に展開されているパッケージを実行します。

詳細については、次を参照してください。[をクラウドにリフト アンド シフトの SQL Server Integration Services のワークロード](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md)です。

これらの新機能では、SQL Server Data Tools (SSDT) 17.2 以降のバージョンを必要とは、SQL Server 2017 年 1 または SQL Server 2016 は必要ありません。 Azure にパッケージを配置する場合、パッケージの展開ウィザードは、パッケージを常に最新のパッケージ形式にアップグレードされます。

## <a name="new-in-the-azure-feature-pack"></a>Azure Feature Pack の新機能

SQL Server の接続性の向上だけでなく、Integration Services Feature Pack for Azure に Azure Data Lake Store のサポートが追加されました。 詳細については、ブログの投稿を参照してください。[新しい Azure 機能パック リリース強化 ADLS 接続](https://blogs.msdn.microsoft.com/ssis/2017/08/29/new-azure-feature-pack-release-strengthening-adls-connectivity/)です。 参照してください[Integration Services (SSIS) の Azure Feature Pack](azure-feature-pack-for-integration-services-ssis.md)です。

## <a name="new-in-sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT) の新機能

SSIS プロジェクトと Visual Studio 2015 または Visual Studio 2017 で 2017年使用して SQL Server バージョン 2012 を対象とするパッケージを開発できます。 詳細については、「[SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)」を参照してください。

## <a name="new-in-ssis-in-sql-server-2017-rc1"></a>SQL Server 2017 RC1 で SSIS の新機能

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>SSIS 用にスケール アウトで追加または変更された機能

-   スケール アウト マスターで高可用性を実現できるようになりました。 SSISDB の Alwayson を有効にして、Windows Server フェールオーバー クラスタ リング設定、サーバーをホストするスケール アウト マスター サービスことができます。 スケール アウト マスターには、この変更を適用することでは、単一障害点を回避して、スケール アウト配置全体の高可用性を実現します。
-   スケール アウト ワーカーの実行ログのフェールオーバー処理が改善されました。 実行ログは、スケール アウト ワーカーが予期せず停止した場合に、ローカル ディスクに保存されます。 後で、作業者が再起動されると、永続化されたログを再読み込みして SSISDB に保存を続行します。
-   ストアド プロシージャ **[catalog].[create_execution]** の *runincluster* パラメーターは、一貫性とわかりやすさを理由に、名前が *runinscaleout* に変更されました。 このパラメーター名の変更は、次の影響を及ぼします。
    -   パラメーターの名前を変更する必要がある場合はスケール アウトでパッケージを実行する既存のスクリプト、 *runincluster*に*runinscaleout* RC1 で作業するスクリプトを作成します。
    -   SQL Server Management Studio (SSMS) 17.1 と以前のバージョンは、RC1 では、スケール アウトでパッケージの実行をトリガーできません。 エラー メッセージ: "*@runincluster* はプロシージャ **create_execution** のパラメーターではありません。" この問題は、SSMS の次のリリースであるバージョン 17.2 で解決されています。 17.2 および SSMS のそれ以降のバージョンでは、スケール アウトで新しいパラメーター名およびパッケージ実行をサポートします。SSMS 17.2 のバージョンを使用できる、問題を回避するまでは、パッケージ実行スクリプトを生成する、既存のバージョンの SSMS を使用して、名前を変更、 *runincluster*パラメーターを*runinscaleout*スクリプト、および、スクリプトを実行します。
-   SSIS カタログに、SSIS パッケージを実行する既定のモードを指定するための新しいグローバル プロパティが追加されました。 呼び出すと、この新しいプロパティが適用されます、 **[カタログ]. [create_execution]**ストアド プロシージャを*runinscaleout*パラメーターを null に設定します。 このモードは、SSIS SQL エージェント ジョブにも適用されます。 SSMS で、または次のコマンドでは、SSISDB ノードのプロパティ ダイアログ ボックスで、新しいグローバル プロパティを設定できます。
    ```sql
    EXEC [catalog].[configure_catalog] @property_name=N'DEFAULT_EXECUTION_MODE', @property_value=1
    ```

## <a name="new-in-ssis-in-sql-server-2017-ctp-21"></a>SQL Server 2017 CTP 2.1 で SSIS の新機能

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>SSIS 用にスケール アウトで追加または変更された機能

-   使用できるように、 **Use32BitRuntime**スケール アウトでの実行をトリガーする場合のパラメーターです。
-   SSISDB をスケール アウトで実行されたパッケージのログのパフォーマンスが改善されました。 イベント メッセージとメッセージ コンテキストのログは、1 つずつではなくバッチ モードで今すぐ SSISDB に書き込まれます。 この機能強化について追加の注意事項を次に示します。        
    - 現在のバージョンの SQL Server Management Studio (SSMS) で一部のレポートでは、スケール アウトで実行するため、これらのログを表示しない現在します。SSMS の次のリリースでサポートされるが予想されます。 影響を受けるレポートが含まれて、*すべての接続*、レポート、*エラー コンテキスト*レポート、および*接続情報*統合サービスのダッシュ ボードのセクションです。
    - 新しい列**event_message_guid**が追加されました。 [カタログ] に参加するのにには、この列を使用します。[event_message_context] ビュー [catalog].[event_messages] を使用する代わりに表示**event_message_id**スケール アウトでの実行のこれらのログを照会するとき。
-   スケール アウト SSIS、それぞれの管理アプリケーションを取得する[SQL Server Management Studio (SSMS) をダウンロード](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)17.1 またはそれ以降。

## <a name="new-in-ssis-in-sql-server-2017-ctp-20"></a>SQL Server 2017 CTP 2.0 での SSIS の新機能

SQL Server 2017 CTP 2.0 では、SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-2017-ctp-14"></a>SQL Server 2017 CTP 1.4 で SSIS の新機能

SQL Server 2017 CTP 1.4 の SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-2017-ctp-13"></a>SQL Server 2017 ctp 1.3 SSIS の新機能

SQL Server 2017 CTP 1.3 では、SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-2017-ctp-12"></a>SQL Server 2017 ctp 1.2 SSIS の新機能

SQL Server 2017 CTP 1.2 では、SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-2017-ctp-11"></a>SQL Server 2017 CTP 1.1 での SSIS の新機能

SQL Server 2017 CTP 1.1 では、SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-2017-ctp-10"></a>SQL Server 2017 CTP 1.0 での SSIS の新機能

### <a name="scale-out-for-ssis"></a>SSIS のスケール アウト

スケール アウト機能により、複数のコンピューターで [!INCLUDE[ssIS_md](../includes/ssis-md.md)] を実行することが簡単になりました。 
   
Scale Out Master と Scale Out Worker をインストールすると、パッケージを配布し、さまざまな Worker で自動的に実行できます。 実行が予期せずに終了した場合、自動的に再試行されます。 また、Master を利用し、すべての実行と Worker が中央管理されます。
   
詳細については、[「Integration Services Scale Out」](../integration-services/scale-out/integration-services-ssis-scale-out.md) を参照してください。
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Microsoft Dynamics オンライン リソースのサポート

OData ソースと OData 接続マネージャーで、Microsoft Dynamics AX Online と Microsoft Dynamics CRM Online の OData フィードに接続できるようになりました。


