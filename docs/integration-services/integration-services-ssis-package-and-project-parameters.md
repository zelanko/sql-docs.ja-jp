---
title: "Integration Services (SSIS) パッケージとプロジェクト パラメーター | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.parameter.f1"
  - "sql13.dts.designer.paramterwindow.f1"
ms.assetid: 9ed9ca8e-8b1e-48d9-907d-285516d6562b
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Integration Services (SSIS) パッケージとプロジェクト パラメーター
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) パラメーターを使用すると、パッケージの実行時に、パッケージ内のプロパティに値を割り当てることができます。 作成することができます *プロジェクトのパラメーターを* プロジェクト レベルでと *パラメーターをパッケージ化* パッケージ レベルです。 プロジェクト パラメーターは、プロジェクトが受け取る外部入力をプロジェクト内の 1 つまたは複数のパッケージに指定するために使用します。 パッケージ パラメーターを使用すると、パッケージを編集したり再配置したりせずにパッケージ実行を変更できます。  
  
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を作成、変更、またはプロジェクト パラメーターを使用して、削除、 **Project.params** ウィンドウです。 作成、変更、およびパッケージ パラメーターを使用して、削除、 **パラメーター** ] タブで、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーです。 新規または既存のパラメーターと関連付けたタスクのプロパティを使用して、 **パラメーター化** ] ダイアログ ボックス。 使用に関する詳細については、 **Project.params** ウィンドウおよび **パラメーター** ] タブを参照してください [パラメーターの作成](../Topic/Create%20Parameters.md)します。 詳細については、 **パラメーター化** ダイアログ ボックスを参照してください [] ダイアログ ボックスのパラメーター化](../Topic/Parameterize%20Dialog%20Box.md)します。  
  
## パラメーターとパッケージ配置モデル  
 通常、パッケージ配置モデルを使用してパッケージを配置する場合、パラメーターではなく構成を使用する必要があります。  
  
 パッケージ配置モデルを使用してパラメーターを含むパッケージを配置し、パッケージを実行した場合、実行時にパラメーターは呼び出されません。 パッケージにパッケージ パラメーターが含まれ、パッケージ内の式でパラメーターが使用されている場合、実行時に結果の値が適用されます。 パッケージにプロジェクト パラメーターが含まれている場合、パッケージの実行は失敗する可能性があります。  
  
## パラメーターとプロジェクト配置モデル  
 ビュー、ストアド プロシージャを使用する Integration Services (SSIS) サーバーにプロジェクトを配置するときに、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] プロジェクトおよびパッケージ パラメーターを管理するための UI です。 詳細については、次の各トピックを参照してください。  
  
-   [ビューと #40";"Integration Services カタログ"と"#41 です。](../integration-services/system-views/views-integration-services-catalog.md)  
  
-   [ストアド プロシージャと #40; Integration Services カタログ & #41 です。](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
  
-   [[構成] ダイアログ ボックス](../Topic/Configure%20Dialog%20Box.md)  
  
-   [[パッケージの実行] ダイアログ ボックス](../Topic/Execute%20Package%20Dialog%20Box.md)  
  
### パラメーター値  
 パラメーターに最大 3 つの型の値を割り当てることができます。 パッケージ実行が開始されると、パラメーターに 1 つの値が使用され、パラメーターはその最終的なリテラル値に解決されます。  
  
 次の表に、値の型の一覧を示します。  
  
|値の名前|説明|値の型|  
|----------------|-----------------|-------------------|  
|実行値|パッケージ実行の特定のインスタンスに割り当てられる値です。 この割り当ては他のすべての値より優先されますが、適用されるのは、パッケージ実行の 1 つのインスタンスのみです|リテラル|  
|サーバーの値|プロジェクトが Integration Services サーバーに配置された後にプロジェクトのスコープ内にあるパラメーターに割り当てられる値です。 この値は、設計上の既定値より優先されます。|リテラルまたは環境変数の参照|  
|設計上の値|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でプロジェクトを作成または編集するときにパラメーターに割り当てられる値です。 この値はプロジェクトと共に保持されます。|リテラル|  
  
 1 つのパラメーターを使用して、複数のパッケージのプロパティに値を割り当てることができます。 1 つのパッケージのプロパティには、1 つのパラメーターの値のみを割り当てることができます。  
  
###  <a name="executions"></a> 実行とパラメーター値  
  *実行* パッケージ実行の 1 つのインスタンスを表すオブジェクトします。 実行を作成するときに、実行パラメーター値など、パッケージの実行に必要なすべての詳細情報を指定します。 既存の実行のパラメーター値を変更することもできます。  
  
 実行パラメーター値を明示的に設定すると、その値はその特定の実行インスタンスにのみ適用できます。 実行値は、サーバーの値または設計上の値の代わりに使用されます。 実行値を明示的に設定せず、サーバーの値が指定されている場合は、サーバーの値が使用されます。  
  
 パラメーターが必須とマークされている場合、サーバーの値または実行値をそのパラメーターに指定する必要があります。 それ以外の場合、対応するパッケージは実行されません。 デザイン時にパラメーターに既定値が設定されていても、プロジェクトが配置されると使用されることはありません。  
  
#### 環境変数  
 パラメーターが環境変数を参照する場合、その変数のリテラル値は、指定した環境参照を通じて解決され、パラメーターに適用されます。 パッケージ実行に使用される最終的なリテラル パラメーター値は、実行パラメーター値と呼ばれます。 使用して、実行の環境参照を指定する、 **Execute** ] ダイアログ ボックス  
  
 プロジェクト パラメーターで環境変数を参照していて、変数のリテラル値を実行時に解決できない場合、設計上の値が使用されます。 サーバーの値は使用されません。  
  
 パラメーター値に割り当てられている環境変数を表示するには、catalog.object_parameters ビューに対してクエリを実行します。 詳細については、次を参照してください。 [catalog.object_parameters & #40 です。SSISDB データベースと #41;](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)します。  
  
#### 実行パラメーター値の決定  
 次の Transact-SQL ビューとストアド プロシージャを使用して、パラメーター値を表示および設定できます。  
  
 [catalog.execution_parameter_values & #40 です。SSISDB データベースと #41;](../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)(ビュー)  
 特定の実行で使用される実際のパラメーター値を示します。  
  
 [catalog.get_parameter_values & #40 です。SSISDB データベースと #41;](../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md) (ストアド プロシージャ)  
 指定されたパッケージと環境参照の実際の値を解決して示します。  
  
 [catalog.object_parameters & #40 です。SSISDB データベースと #41;](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) (ビュー)  
 設計上の既定値とサーバーの既定値を含め、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログのすべてのパッケージおよびプロジェクトのパラメーターとプロパティを表示します。  
  
 [catalog.set_execution_parameter_value & #40 です。SSISDB データベースと #41 です。](../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログの実行のインスタンスにパラメーターの値を設定します。  
  
 使用することも、 **パッケージ実行** ] ダイアログ ボックスで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] パラメーター値を変更します。 詳細については、次を参照してください。 [パッケージ] ダイアログ ボックスの実行](../Topic/Execute%20Package%20Dialog%20Box.md)します。  
  
 Dtexec を使用することもできます。 **/Parameter** パラメーター値を変更するにはオプションです。 詳細については、「 [dtexec Utility](../integration-services/packages/dtexec-utility.md)」を参照してください。  
  
### パラメーターの検証  
 パラメーター値を解決できない場合、対応するパッケージ実行は失敗します。 エラーを回避するために、ことを検証するプロジェクトとパッケージを使用して、 **検証** ] ダイアログ ボックスで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]します。 検証を使用すると、すべてのパラメーター値に必要な値が設定されているか、または特定の環境参照で必要な値を解決できるかを確認できます。 検証では、その他の一般的なパッケージの問題も確認されます。  
  
 詳細については、次を参照してください。 [を確認するダイアログ ボックス](../integration-services/service/validate-dialog-box.md)します。  
  
### パラメーターの例  
 この例ではという名前のパラメーター **pkgOptions** が存在するパッケージのオプションを指定するために使用されます。  
  
 設計時に、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で作成されたパラメーターには、既定値 1 が割り当てられます。 この既定値は、設計上の既定値と呼ばれます。 プロジェクトが SSISDB カタログに配置されに対応するパッケージのプロパティは、このパラメーターにその他の値が割り当てられていない場合、 **pkgOptions** パラメーターが指定値が 1 のパッケージの実行中です。 設計上の既定値は、プロジェクトと共にライフ サイクル全体で保持されます。  
  
 パッケージの実行の特定のインスタンスは、次のように準備が整ったときに値 5 が割り当てられている、 **pkgOptions** パラメーター。 この値は実行値と呼ばれます。これは、その特定の実行インスタンスのパラメーターにのみ適用されるためです。 ときに、実行の開始に対応するパッケージ プロパティ、 **pkgOptions** パラメーターに値 5 が割り当てられます。  
  
## 関連タスク  
 [パラメーターの作成](../Topic/Create%20Parameters.md)  
  
 [プロジェクトを配置した後にパラメーターの値を設定する](../Topic/Set%20Parameter%20Values%20After%20the%20Project%20Is%20Deployed.md)  
  
## 関連コンテンツ  
 ブログ エントリ「 [SSIS 簡単なヒント: 必要なパラメーター](http://go.microsoft.com/fwlink/?LinkId=239781), mattmasson.com のブログ「します。  
  
  