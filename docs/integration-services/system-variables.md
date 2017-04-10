---
title: "システム変数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンテナー [Integration Services], 変数"
  - "タスク [Integration Services], 変数"
  - "システム変数 [Integration Services]"
  - "イベント ハンドラー [Integration Services], 変数"
  - "変数 [Integration Services], システム"
ms.assetid: efecd0d4-1489-4eba-a8fe-275d647058b8
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# システム変数
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、実行中のパッケージとそのオブジェクトに関する情報を格納する、システム変数のセットが用意されています。 これらの変数は、式およびプロパティ式の内部で使用でき、パッケージ、コンテナー、タスク、およびイベント ハンドラーをカスタマイズできます。  
  
 すべての変数 (システム変数とユーザー定義変数) を SQL 実行タスクが使用するパラメーター バインドで使用して、パラメーターに変数をマップできます。  
  
## パッケージ用システム変数  
 次の表では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] がパッケージ用に提供するシステム変数について説明します。  
  
|システム変数|データ型|Description|  
|---------------------|---------------|-----------------|  
|**CancelEvent**|Int32|タスクがシグナルを送信して実行を停止する必要があることを示す、Windows イベント オブジェクトへのハンドルです。|  
|**ContainerStartTime**|DateTime|コンテナーの開始時刻です。|  
|**CreationDate**|DateTime|パッケージが作成された日付です。|  
|**CreatorComputerName**|文字列|パッケージが作成されたコンピューターです。|  
|**CreatorName**|文字列|パッケージの構築者の名前です。|  
|**ExecutionInstanceGUID**|文字列|実行中のパッケージのインスタンスの一意識別子です。|  
|**FailedConfigurations**|文字列|失敗したパッケージ構成の名前。|  
|**IgnoreConfigurationsOnLoad**|ブール値|パッケージを読み込むときにパッケージ構成を無視するかどうかを示します。|  
|**InteractiveMode**|ブール値|パッケージが対話モードで実行されているかどうかを示します。 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを実行中の場合、このプロパティは **True** に設定されます。 **DTExec** コマンド プロンプト ユーティリティを使用してパッケージを実行中の場合、プロパティは **False** に設定されます。|  
|**LocaleId**|Int32|パッケージで使用するロケールです。|  
|**MachineName**|文字列|パッケージが実行されているコンピューターの名前です。|  
|**OfflineMode**|ブール値|パッケージがオフライン モードかどうかを示します。 オフライン モードでは、データ ソースへの接続は取得されません。|  
|**PackageID**|文字列|パッケージの一意識別子です。|  
|**PackageName**|文字列|パッケージの名前です。|  
|**StartTime**|DateTime|パッケージの実行を開始した時刻です。|  
|**ServerExecutionID**|Int64|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーで実行されるパッケージの実行 ID です。<br /><br /> 既定値はゼロです。 この値が変更されるのは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーで ISServerExec によってパッケージが実行される場合のみです。 子パッケージがある場合は、この値が親パッケージから子パッケージに渡されます。|  
|**UserName**|文字列|パッケージを開始したユーザーのアカウントです。 ユーザー名は、ドメイン名によって修飾されます。|  
|**VersionBuild**|Int32|パッケージのバージョンです。|  
|**VersionComment**|文字列|パッケージ バージョンについてのコメント。|  
|**VersionGUID**|文字列|バージョンの一意識別子です。|  
|**VersionMajor**|Int32|パッケージのメジャー バージョン。|  
|**VersionMinor**|Int32|パッケージのマイナー バージョン。|  
  
## コンテナー用システム変数  
 次の表では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が、For ループ コンテナー、Foreach ループ コンテナー、およびシーケンス コンテナー用に提供するシステム変数について説明します。  
  
|システム変数|データ型|Description|コンテナー|  
|---------------------|---------------|-----------------|---------------|  
|**LocaleId**|Int32|コンテナーが使用するロケールです。|For ループ コンテナー<br /><br /> Foreach ループ コンテナー<br /><br /> シーケンス コンテナー|  
  
## タスク用システム変数  
 次の表では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] がタスク用に提供するシステム変数について説明します。  
  
|システム変数|データ型|Description|  
|---------------------|---------------|-----------------|  
|**CreationName**|文字列|タスクの名前です。|  
|**LocaleId**|Int32|タスクが使用するロケールです。|  
|**TaskID**|文字列|タスク インスタンスの一意識別子です。|  
|**TaskName**|文字列|タスク インスタンスの名前です。|  
|**TaskTransactionOption**|Int32|タスクが使用するトランザクションのオプションです。|  
  
## イベント ハンドラー用システム変数  
 次の表では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] がイベント ハンドラー用に提供するシステム変数について説明します。 すべての変数がすべてのイベント ハンドラーで使用できるわけではありません。  
  
|システム変数|データ型|Description|イベント ハンドラー|  
|---------------------|---------------|-----------------|-------------------|  
|**キャンセル**|ブール値|エラー、警告、またはクエリのキャンセルが発生したときに、イベント ハンドラーが実行を停止するかどうかを示します。|OnError イベント ハンドラー<br /><br /> OnWarning イベント ハンドラー<br /><br /> OnQueryCancel イベント ハンドラー|  
|**ErrorCode**|Int32|エラー識別子です。|OnError イベント ハンドラー<br /><br /> OnInformation イベント ハンドラー<br /><br /> OnWarning イベント ハンドラー|  
|**ErrorDescription**|文字列|エラーの説明。|OnError イベント ハンドラー<br /><br /> OnInformation イベント ハンドラー<br /><br /> OnWarning イベント ハンドラー|  
|**ExecutionStatus**|ブール値|現在の実行ステータスです。|OnExecStatusChanged イベント ハンドラー|  
|**ExecutionValue         **|DBNull|実行値です。|OnTaskFailed イベント ハンドラー|  
|**LocaleId**|Int32|イベント ハンドラーが使用するロケールです。|すべてのイベント ハンドラー|  
|**PercentComplete**|Int32|完了済みの作業の割合です。|OnProgress イベント ハンドラー|  
|**ProgressCountHigh**|Int32|OnProgress イベントによって処理される操作の総数を示す、64 ビット値の上位部分です。|OnProgress イベント ハンドラー|  
|**ProgressCountLow**|Int32|OnProgress イベントによって処理される操作の総数を示す、64 ビット値の下位部分です。|OnProgress イベント ハンドラー|  
|**ProgressDescription**|文字列|進行状況の説明です。|OnProgress イベント ハンドラー|  
|**Propagate**|ブール値|イベントが、上位レベルのイベント ハンドラーに反映されるかどうかを示します。<br /><br /> 注: 変数 **Propagate** の値は、パッケージの検証中は無視されます。 子パッケージ内で **Propagate** を **False** に設定しても、イベントは親パッケージに反映されます。|すべてのイベント ハンドラー|  
|**SourceDescription**|文字列|イベントを発生させたイベント ハンドラー内の実行可能ファイルの説明です。|すべてのイベント ハンドラー|  
|**[SourceID]**|文字列|イベントを発生させたイベント ハンドラー内の実行可能ファイルの一意識別子です。|すべてのイベント ハンドラー|  
|**[SourceName]**|文字列|イベントを発生させたイベント ハンドラー内の実行可能ファイルの名前です。|すべてのイベント ハンドラー|  
|**VariableDescription**|文字列|変数の説明です。|OnVariableValueChanged イベント ハンドラー|  
|**VariableID**|文字列|変数の一意識別子です。|OnVariableValueChanged イベント ハンドラー|  
  
## パラメーター バインドにおけるシステム変数  
 パッケージの実行時に、システム変数の値をテーブルに保存すると役立つことがよくあります。 たとえば、テーブルを動的に作成し、このテーブルを作成したパッケージ実行インスタンスの GUID をテーブル列に書き込むパッケージなどです。  
  
 システム変数を使用して、SQL 実行タスクが使用する SQL ステートメントのパラメーターにマップする場合、各パラメーター バインドのデータ型を、システム変数のデータ型に設定することが重要です。 このように設定しないと、システム変数の値が誤って解釈されることがあります。 たとえば、 **ExecutionInstanceGUID** システム変数は文字列データ型で、実行中のパッケージのインスタンスの GUID の文字列表現を保持しますが、パラメーター バインドに GUID データ型を使用すると、パッケージのインスタンスの GUID は誤って解釈されます。  
  
 この規則は、ユーザー定義変数にも当てはまります。 ただし、システム変数のデータ型は変更できないため、システム変数を使用する場合はそのデータ型に合わせた調整が必要ですが、ユーザー定義変数にはそれに比べると高い柔軟性があります。 パラメーター バインドで使用するユーザー定義変数は、通常、マップ先パラメーターのデータ型と互換性のあるデータ型で定義します。  
  
## 関連タスク  
 [クエリ パラメーターを SQL 実行タスクの変数にマップする方法](../Topic/Map%20Query%20Parameters%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
  