---
title: "Integration Services パッケージによってログに記録されるイベント | Microsoft Docs"
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
  - "パッケージ [Integration Services], イベント"
  - "イベント[Integration Services], パッケージ"
ms.assetid: 55a0951a-46f3-4f0f-9972-74cec9cc26b7
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# Integration Services パッケージによってログに記録されるイベント
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、各種のイベント メッセージを Windows アプリケーション イベント ログに記録します。 これらのメッセージは、パッケージの起動時、パッケージの停止時、および特定の問題の発生時にログに記録されます。  
  
 このトピックでは、アプリケーション イベント ログに記録される一般的なイベント メッセージについて説明します。 既定では、パッケージのログ記録が有効になっていない場合でも、一部のメッセージはログに記録されます。 それ以外のメッセージは、パッケージのログ記録が有効になっている場合にのみログに記録されます。 既定でログに記録されたか、ログ記録を有効にしたことによってログに記録されたかに関係なく、これらのメッセージのイベント ソースは SQLISPackage になります。  
  
 SSIS パッケージの実行方法に関する一般的な情報については、「[プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/ms141708.aspx)」をご覧ください。  
  
 パッケージの実行に関するトラブルシューティング方法については、「[パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」をご覧ください。  
  
## パッケージの状態に関するメッセージ  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを実行すると、通常、そのパッケージの進行状況と状態に関するさまざまなメッセージがログに記録されます。 次の表に、そのメッセージの一覧を示します。  
  
> [!NOTE]  
>  パッケージのログ記録が有効になっていない場合でも、次の表に示すメッセージはログに記録されます。  
  
|イベント ID|シンボル名|テキスト|注|  
|--------------|-------------------|----------|-----------|  
|12288|DTS_MSG_PACKAGESTART|パッケージ "" が起動されました。|パッケージの実行が開始されました。|  
|12289|DTS_MSG_PACKAGESUCCESS|パッケージ "" が正常に完了しました。|パッケージが正常に実行され、現在は実行されていません。|  
|12290|DTS_MSG_PACKAGECANCEL|パッケージ "%1!s!" は取り消されました。|パッケージが取り消されたため、現在は実行されていません。|  
|12291|DTS_MSG_PACKAGEFAILURE|パッケージ "" は失敗しました。|パッケージは正常に実行できずに、実行を停止しました。|  
  
 既定では、新規インストールで、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はパッケージの実行に関連する特定のイベントをアプリケーション イベント ログに記録しないように構成されます。 現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ コレクター機能を使用すると、この設定により、大量のイベント ログ エントリは生成されません。 ログに記録されないイベントは、EventID 12288 の "パッケージが起動されました。" や EventID 12289 の "パッケージが正常に完了しました。" です。 これらのイベントをアプリケーション イベント ログに記録するには、レジストリを編集用に開きます。 次に、レジストリ内で HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS ノードを見つけ、LogPackageExecutionToEventLog 設定の DWORD 値を 0 から 1 に変更します。 ただし、アップグレード インストールでは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はこれらの 2 つのイベントをログに記録するように構成されます。 ログを無効にするには、LogPackageExecutionToEventLog 設定の値を 1 から 0 に変更します。  
  
## パッケージのログ記録に関連付けられているメッセージ  
 パッケージのログ記録が有効になっている場合、アプリケーション イベント ログは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのオプションのログ記録機能によってサポートされる記録先の 1 つです。 詳細については、「[Integration Services (SSIS) のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」をご覧ください。  
  
 パッケージのログ記録が有効になっていて、ログの場所がアプリケーション イベント ログである場合は、次の情報に関連するエントリがログに記録されます。  
  
-   実行中のパッケージの段階に関するメッセージ  
  
-   パッケージの実行中に発生する特定のイベントに関するメッセージ  
  
### パッケージ実行の段階に関するメッセージ  
  
|イベント ID|シンボル名|テキスト|注|  
|--------------|-------------------|----------|-----------|  
|12544|DTS_MSG_EVENTLOGENTRY|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|アプリケーション イベント ログへのログ記録を構成すると、さまざまなメッセージがこの一般的な形式で記録されます。|  
|12556|DTS_MSG_EVENTLOGENTRY_PACKAGESTART|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|パッケージが開始されました。|  
|12547|DTS_MSG_EVENTLOGENTRY_PREVALIDATE|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|オブジェクトの検証が開始されようとしています。|  
|12548|DTS_MSG_EVENTLOGENTRY_POSTVALIDATE|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|オブジェクトの検証が完了しました。|  
|12552|DTS_MSG_EVENTLOGENTRY_PROGRESS|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|この汎用メッセージはパッケージの進行状況を報告します。|  
|12546|DTS_MSG_EVENTLOGENTRY_POSTEXECUTE|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|オブジェクトの処理が完了しました。|  
|12557|DTS_MSG_EVENTLOGENTRY_PACKAGEEND|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|パッケージの実行が完了しました。|  
  
### 発生したイベントに関するメッセージ  
 次の表に、イベントの結果として出力されるメッセージの一部を示します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用されるエラー メッセージ、警告メッセージ、および情報メッセージの詳細な一覧については、「[Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)」をご覧ください。  
  
|イベント ID|シンボル名|テキスト|注|  
|--------------|-------------------|----------|-----------|  
|12251|DTS_MSG_EVENTLOGENTRY_TASKFAILED|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|タスクは失敗しました。|  
|12250|DTS_MSG_EVENTLOGENTRY_ERROR|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|このメッセージは発生したエラーを報告します。|  
|12249|DTS_MSG_EVENTLOGENTRY_WARNING|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|このメッセージは発生した警告を報告します。|  
|12258|DTS_MSG_EVENTLOGENTRY_INFORMATION|イベント名: %1%r メッセージ: %9%r 演算子: %2%r ソース名: %3%r ソース ID: %4%r 実行 ID: %5%r 開始時刻: %6%r 終了時刻: %7%r データ コード: %8|このメッセージは、エラーまたは警告に関連しない情報メッセージです。|  
  
## 関連タスク  
 リアルタイムでログ エントリを表示する方法については、「[[ログ イベント] ウィンドウでログ エントリを表示する](../Topic/View%20Log%20Entries%20in%20the%20Log%20Events%20Window.md)」をご覧ください。  
  
## 参照  
 [Integration Services サービスによってログに記録されるイベント](../../integration-services/service/events-logged-by-the-integration-services-service.md)  
  
  