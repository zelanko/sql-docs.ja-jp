---
title: "Integration Services (SSIS) パッケージの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services パッケージ, 実行"
  - "SSIS パッケージ, 実行"
  - "パッケージ [Integration Services]、実行"
  - "SQL Server Integration Services パッケージ, 実行"
  - "パッケージの実行 [Integration Services]"
  - "パッケージの実行 [Integration Services]"
  - "Integration Services, (「Integration Services パッケージ」も参照)"
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
caps.latest.revision: 65
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Integration Services (SSIS) パッケージの実行
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを実行するには、それらのパッケージの格納場所に応じていくつかのツールのうちの 1 つを使用できます。 次の表にツールを示します。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにパッケージを格納するには、プロジェクト配置モデルを使用してプロジェクトをサーバーに配置します。 詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../../integration-services/packages/deploy-projects-to-integration-services-server.md)」を参照してください。  
  
 SSIS パッケージ ストア、msdb データベース、またはファイル システムにパッケージを格納するには、パッケージ配置モデルを使用します。 詳細については、「[レガシー パッケージの配置 &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)」を参照してください。  
  
|ツール|Integration Services サーバーに格納されているパッケージ|SSIS パッケージ ストアまたは msdb データベースに格納されているパッケージ|ファイル システムに格納されているパッケージ (SSIS パッケージ ストアに含まれる場所の範囲外)|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|いいえ|いいえ<br /><br /> ただし、msdb データベースを含む [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストアからプロジェクトに既存のパッケージを追加できます。 この方法でプロジェクトに既存のパッケージを追加すると、ファイル システム内にパッケージのローカル コピーが作成されます。|可|  
|**SQL Server Management Studio (Integration Services サーバーをホストするデータベース エンジンのインスタンスに接続している場合)**<br /><br /> 詳細については、「 [[パッケージの実行] ダイアログ ボックス](../Topic/Execute%20Package%20Dialog%20Box.md)」を参照してください。|可|いいえ<br /><br /> ただし、これらの場所からサーバーにパッケージをインポートできます。|いいえ<br /><br /> ただし、ファイル システムからサーバーにパッケージをインポートできます。|
|**SQL Server Management Studio (Scale Out Master として有効になっている Integration Services サーバーをホストするデータベース エンジンのインスタンスに接続している場合)**<br /><br /> 詳しくは、「[Integration Services (SSIS) Scale Out でパッケージを実行する](../../integration-services/run-packages-in-integration-services-ssis-scale-out.md)」をご覧ください。|可|不可|いいえ|
|**SQL Server Management Studio (SSIS パッケージ ストアを管理する Integration Services サービスに接続している場合)**|いいえ|可|いいえ<br /><br /> ただし、ファイル システムから [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストアにパッケージをインポートできます。|  
|**dtexec**<br /><br /> 詳しくは、「 [dtexec Utility](../../integration-services/packages/dtexec-utility.md)」をご覧ください。|可|可|可|  
|**dtexecui**<br /><br /> 詳細については、「[パッケージ実行ユーティリティ &#40;DtExecUI&#41; の UI リファレンス](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md)」を参照してください。|いいえ|可|はい|  
|**SQL Server エージェント**<br /><br /> パッケージのスケジュールを設定するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを使用します。<br /><br /> 詳細については、「 [パッケージに対する SQL Server エージェント ジョブ](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)」を参照してください。|可|可|可|  
|**組み込みのストアド プロシージャ**<br /><br /> 詳細については、「[catalog.start_execution &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)」を参照してください。|可|不可|いいえ|  
|**API (** <xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間の型およびメンバーを使用)|可|不可|いいえ|  
|**API (** <xref:Microsoft.SqlServer.Dts.Runtime> 名前空間の型およびメンバーを使用)|現時点ではいいえ|可|可|  
  
## <a name="execution-and-logging"></a>実行とログ  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージではログ記録を有効にできるので、実行時情報をログ ファイルに保存できます。 詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」を参照してください。  
  
 操作レポートを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置され、実行されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを監視できます。 レポートは [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で利用できます。 詳細については、「 [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
-   [SQL Server エージェントを使用してパッケージのスケジュールを設定する](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md)  
  
-   [SQL Server Data Tools でのパッケージの実行](../../integration-services/packages/run-a-package-in-sql-server-data-tools.md)  
  
-   [SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>参照  
 [dtexec ユーティリティ](../../integration-services/packages/dtexec-utility.md)   
[SQL Server インポートおよびエクスポート ウィザードを起動する](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)
  
  