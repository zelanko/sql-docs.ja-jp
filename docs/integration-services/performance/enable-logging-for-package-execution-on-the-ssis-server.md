---
title: "SSIS サーバーでのパッケージ実行のログ記録を有効にする | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SSIS.SSMS.ISMANAGECUSTOMIZEDLOGGINGLEVEL.F1"
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# SSIS サーバーでのパッケージ実行のログ記録を有効にする
  このトピックでは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置したパッケージを実行するときに、パッケージのログ記録レベルを設定または変更する方法について説明します。 パッケージを実行するときに設定したログ記録レベルは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]での設計時に構成したパッケージのログ記録レベルよりも優先されます。 詳細については、「[SQL Server Data Tools でパッケージのログ記録を有効にする](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)」を参照してください。  
  
 SQL Server の **[サーバーのプロパティ]** のサーバーの **[ログ記録レベル]** プロパティで、既定のサーバー全体のログ記録レベルを選択できます。 このトピックで説明している組み込みのログ記録レベルのいずれかを選択するか、既存のカスタマイズしたログ記録レベルを選択できます。 選択したログ記録レベルは、既定で SSIS カタログに展開されているすべてのパッケージに適用されます。 また、既定で SSIS パッケージを実行する SQL エージェント ジョブにも適用されます。  
  
 また、次のいずれかの方法で、個々のパッケージのログ記録レベルを指定することもできます。 このトピックでは最初の方法について説明します。  
  
-   [パッケージの実行] ダイアログ ボックスを使用してパッケージ実行インスタンスを構成する  
  
-   [catalog.set_execution_parameter_value &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md) を使用して、実行のインスタンスのパラメーターを設定する  
  
-   [新しいジョブ ステップ] ダイアログ ボックスを使用してパッケージ実行用の SQL Server エージェント ジョブを構成する  
  
## [パッケージの実行] ダイアログ ボックスを使用して、パッケージのログ記録レベルを設定します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、パッケージに移動します。  
  
2.  パッケージを右クリックし、**[実行]** をクリックします。  
  
3.  **[パッケージの実行]** ダイアログ ボックスで、 **[詳細設定]** タブをクリックします。  
  
4.  **[ログ記録レベル]**で、ログ記録レベルを選択します。 このトピックでは、使用できる値について説明します。  
  
5.  他のパッケージの構成を完了し、 **[OK]** をクリックしてパッケージを実行します。  
  
## ログ記録レベルを選択する  
 次の組み込みレベルを使用できます。 また、既存のカスタマイズされたログ記録レベルを選択することもできます。 このトピックでは、カスタマイズのログ記録レベルについて説明します。  
  
|[ログ記録レベル]|Description|  
|-------------------|-----------------|  
|なし|ログ記録をオフにします。 パッケージの実行状態のみがログに記録されます。|  
|基本|カスタム イベントと診断イベントを除く、すべてのイベントをログに記録します。 これが既定値です。|  
|RuntimeLineage|データ フロー内の系列情報を追跡するために必要なデータを収集します。 この系列情報を解析して、タスク間の系列の関係をマッピングできます。 ISV や開発者は、この情報を利用して、ユーザー設定の系列マッピング ツールを構築できます。|  
|パフォーマンス|パフォーマンス統計、および OnError イベントと OnWarning のイベントのみをログに記録します。<br /><br /> **"実行のパフォーマンス"** レポートは、パッケージ データ フロー コンポーネントのアクティブな時間と合計時間を示します。 この情報は、最後のパッケージの実行のログ記録レベルが **[パフォーマンス]** または **[詳細]**に設定されていた場合にのみ表示されます。 詳細については、「 [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md)」を参照してください。<br /><br /> [catalog.execution_component_phases](../../integration-services/system-views/catalog-execution-component-phases.md) ビューは、実行の各フェーズでのデータ フロー コンポーネントの開始時刻と終了時刻を表示します。 これらのコンポーネントの情報は、パッケージの実行のログ記録レベルが **[パフォーマンス]** または **[詳細]**に設定されている場合にのみ、このビューに表示されます。|  
|[詳細]|カスタム イベントと診断イベントを含む、すべてのイベントをログに記録されます。<br /><br /> カスタム イベントには、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] タスクによってログに記録されるイベントが含まれます。 カスタム イベントの詳細については、「 [Custom Messages for Logging](../../integration-services/performance/custom-messages-for-logging.md)」を参照してください。<br /><br /> **DiagnosticEx** イベントは、診断イベントの例です。 パッケージ実行タスクで子パッケージを実行するたびに、このイベントは、子パッケージに渡されたパラメーター値をキャプチャします。<br /><br /> また、**DiagnosticEx** イベントを使用すると、行レベルのエラーが発生した列名も取得できます。 このイベントは、データ フロー系列マップをログに書き込みます。 エラー出力でキャプチャされた列識別子を使用して、この系列マップの列名を調べることができます。  詳細については、「 [Error Handling in Data](../../integration-services/data-flow/error-handling-in-data.md)」を参照してください。<br /><br /> **DiagnosticEx** のメッセージ列の値は XML テキストです。 パッケージ実行のメッセージ テキストを表示するには、[catalog.operation_messages &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md) ビューのクエリを実行します。 **DiagnosticEx** イベントでは XML 出力に含まれる空白が維持されないので、ログのサイズを軽減できます。 読みやすくするために、XML 書式と構文の強調表示をサポートする XML エディター (たとえば Visual Studio) にログをコピーします。<br /><br /> [catalog.execution_data_statistics](../../integration-services/system-views/catalog-execution-data-statistics.md) ビューは、パッケージ実行で、データ フロー コンポーネントが下流コンポーネントへデータを送信するたびに 1 行を表示します。 ビューにこの情報を取得するには、ログ記録レベルを **[詳細]** に設定する必要があります。|  
  
## [カスタマイズされたログ記録レベルの管理] ダイアログ ボックスを使用して、カスタマイズされたログ記録レベルを作成して管理する  
 必要な統計情報とイベントのみを収集するカスタマイズされたログ記録レベルを作成できます。 また、必要に応じて、変数値、接続文字列、コンポーネントのプロパティなど、イベントのコンテキストもキャプチャできます。 パッケージを実行するときに、組み込みのログ記録レベルを選択できる場所であればどこでも、カスタマイズされたログ記録レベルを選択できます。  
  
> [!TIP]  
>  パッケージ変数の値をキャプチャするには、変数の **IncludeInDebugDump** プロパティを **True** に設定する必要があります。  
  
1.  カスタマイズされたログ記録レベルを作成および管理するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、SSISDB データベースを右クリックし、**[カスタマイズされたログ記録レベル]** を選択し、**[カスタマイズされたログ記録レベルの管理]** ダイアログ ボックスを開きます。 **[カスタマイズされたログ記録レベル]** リストには、既存のカスタマイズされたログ記録レベルがすべて含まれています。  
  
2.  新しいカスタマイズされたログ記録レベルを **作成** するには、 **[作成]**をクリックし、名前と説明を入力します。 **[統計情報]** タブと **[イベント]** タブで、収集する統計情報とイベントを選択します。 **[イベント]** タブで、必要に応じて個々のイベントについて **[コンテキストを含める]** を選択します。 **[保存]**をクリックします。  
  
3.  既存のカスタマイズされたログ記録レベルを **更新** するには、リストから選択し、再構成して **[保存]**をクリックします。  
  
4.  既存のカスタマイズされたログ記録レベルを **削除** するには、リストから選択し、 **[削除]**をクリックします。  
  
 **カスタマイズされたログ記録レベルのアクセス許可**  
  
-   SSISDB データベースのすべてのユーザーは、パッケージの実行時に、カスタマイズされたログ記録レベルを表示し、カスタマイズされたログ記録レベルを選択できます。  
  
-   ssis_admin 管理者または sysadmin ロールのユーザーのみが、カスタマイズされたログ記録レベルの作成、更新、または削除を行うことができます。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)   
 [SQL Server Data Tools でパッケージのログ記録を有効にする](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)  
  
  