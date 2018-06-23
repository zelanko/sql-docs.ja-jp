---
title: プロパティ式における列挙定数 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], expressions
- dynamic properties
- updating package properties
- enumerated constants [Integration Services]
- property expressions [Integration Services]
ms.assetid: a4418315-38e2-4ad3-8784-576163b25d6f
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a9a69fcddc41c72a12bec05e224ce3c0c5d70fdc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173610"
---
# <a name="enumerated-constants-in-property-expressions"></a>プロパティ式における列挙定数
  プロパティ式に列挙子メンバー リストの値が含まれている場合、この式ではメンバーの表示名ではなく、列挙子メンバーの数値を使用する必要があります。 たとえば、式の設定、`LoggingMode`プロパティして、表示名 Disabled ではなく、数値 2 を使用する必要があります。  
  
 このトピックでは、プロパティ式でメンバーがよく使用される列挙子の表示名に対応した数値のみを示します。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルには、パッケージをプログラムで構築したり、タスクやデータ フロー コンポーネントなどのカスタム パッケージ要素をコード化する際に使用する列挙子が多数追加されています。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のプロパティ ウィンドウには、パッケージとパッケージ オブジェクトのカスタム プロパティに加えて、パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーで使用できる一連のプロパティが含まれています。 列挙子から値によって設定される共通プロパティ (`ForceExecutionResult`、`LoggingMode`、`IsolationLevel`、および `Transaction Option`) の一覧については、「共通プロパティ」を参照してください。  
  
 次の各セクションでは、列挙定数について説明します。  
  
 [[パッケージ]](#Package)  
  
 [Foreach ループ列挙子](#Foreach)  
  
 [処理手順](#Tasks)  
  
 [メンテナンス プランのタスク](#MaintenancePlanTasks)  
  
 [共通プロパティ](#CommonProperties)  
  
##  <a name="Package"></a> [パッケージ]  
 次の表は、列挙子からの値を使用して設定する、パッケージのプロパティの表示名とそれに対応する数値を示します。  
  
 `PackageType` プロパティ-から値を使用して設定、`DTSPackageType`列挙します。  
  
|DTSPackageType の表示名|数値|  
|-------------------------------------|-------------------|  
|既定|0|  
|DTSWizard|1|  
|DTSDesigner|2|  
|SQLReplication|3|  
|DTSDesigner100|5|  
|SQLDBMaint|6|  
  
 `CheckpointUsage` プロパティ-から値を使用して設定、`DTSCheckpointUsage`列挙します。  
  
|DTSCheckpointUsage の表示名|数値|  
|-----------------------------------------|-------------------|  
|Never|0|  
|IfExists|1|  
|毎回|2|  
  
 `PackagePriorityClass` プロパティ-から値を使用して設定、`DTSPriorityClass`列挙します。  
  
|DTSPriorityClass の表示名|数値|  
|---------------------------------------|-------------------|  
|既定|0|  
|AboveNormal|1|  
|標準|2|  
|BelowNormal|3|  
|Idle|4|  
  
 `ProtectionLevel` プロパティ-から値を使用して設定、`DTSProtectionLevel`列挙します。  
  
|DTSProtectionLevel の表示名|数値|  
|-----------------------------------------|-------------------|  
|DontSaveSensitive|0|  
|EncryptSensitiveWithUserKey|1|  
|EncryptSensitiveWithPassword|2|  
|EncryptAllWithPassword|3|  
|EncryptAllWithUserKey|4|  
|ServerStorage|5|  
  
##  <a name="PrecedenceConstraints"></a> 優先順位制約  
 `EvalOp` プロパティ-から値を使用して設定、`DTSPrecedenceEvalOp`列挙します。  
  
|DTSPrecedenceEvalOp の表示名|数値|  
|------------------------------------------|-------------------|  
|式|1|  
|制約|2|  
|ExpressionAndConstraint|3|  
|ExpressionOrConstraint|4|  
  
 `Value` プロパティ-から値を使用して設定、`DTSExecResult`列挙します。  
  
|表示名|数値|  
|-------------------|-------------------|  
|成功|0|  
|失敗|1|  
|Completion|2|  
|Canceled|3|  
  
##  <a name="Foreach"></a> Foreach ループ列挙子  
 Foreach ループには、プロパティ式で設定できるプロパティを含む一連の列挙子があります。  
  
### <a name="foreach-ado-enumerator"></a>Foreach ADO 列挙子  
 `Type` プロパティ-から値を使用して設定、`ADOEnumerationType`列挙します。  
  
|ADOEnumerationType の表示名|数値|  
|-----------------------------------------|-------------------|  
|EnumerateTables|0|  
|EnumerateAllRows|1|  
|EnumerateRowsInFirstTable|2|  
  
### <a name="foreach-nodelist-enumerator"></a>Foreach Nodelist 列挙子  
 `SourceDocumentType`、 `InnerXPathStringSourceType`、および**OuterXPathStringSourceType**プロパティ — から値を使用して設定、`SourceType`列挙します。  
  
|SourceType の表示名|数値|  
|---------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
|DirectInput|2|  
  
 `EnumerationType` プロパティ-から値を使用して設定、`EnumerationType`列挙します。  
  
|EnumerationType の表示名|数値|  
|--------------------------------------|-------------------|  
|Navigator|0|  
|ノード|1|  
|NodeText|2|  
|ElementCollection|3|  
  
 `InnerElementType` プロパティ-から値を使用して設定、`InnerElementType`列挙します。  
  
|InnerElementType の表示名|数値|  
|---------------------------------------|-------------------|  
|Navigator|0|  
|ノード|1|  
|NodeText|2|  
  
##  <a name="Tasks"></a> 処理手順  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、プロパティ式で設定できるプロパティを含む多くのタスクが含まれています。  
  
### <a name="analysis-services-execute-ddl-task"></a>Analysis Services DDL 実行タスク  
 `SourceType` プロパティ-から値を使用して設定、`DDLSourceType`列挙します。  
  
|DDLSourceType の表示名|数値|  
|------------------------------------|-------------------|  
|DirectInput|0|  
|[FileConnection]|1|  
|変数|2|  
  
### <a name="bulk-insert-task"></a>一括挿入タスク  
 `DataFileType` プロパティ-から値を使用して設定、`DTSBulkInsert_DataFileType`列挙します。  
  
|DTSBulkInsert_DataFileType の表示名|数値|  
|--------------------------------------------------|-------------------|  
|DTSBulkInsert_DataFileType_Char|0|  
|DTSBulkInsert_DataFileType_Native|1|  
|DTSBulkInsert_DataFileType_WideChar|2|  
|DTSBulkInsert_DataFileType_WideNative|3|  
  
### <a name="execute-sql-task"></a>SQL 実行タスク  
 `ResultSetType` プロパティ-から値を使用して設定、`ResultSetType`列挙します。  
  
|ResultSetType の表示名|数値|  
|------------------------------------|-------------------|  
|ResultSetType_None|1|  
|ResultSetType_SingleRow|2|  
|ResultSetType_Rowset|3|  
|ResultSetType_XML|4|  
  
 `SqlStatementSourceType` プロパティ-から値を使用して設定、`SqlStatementSourceType`列挙します。  
  
|SqlStatementSourceType の表示名|数値|  
|---------------------------------------------|-------------------|  
|DirectInput|1|  
|[FileConnection]|2|  
|変数|3|  
  
### <a name="file-system-task"></a>ファイル システム タスク  
 `Operation` プロパティ-から値を使用して設定、`DTSFileSystemOperation`列挙します。  
  
|DTSFileSystemOperation の表示名|数値|  
|---------------------------------------------|-------------------|  
|CopyFile|0|  
|MoveFile|1|  
|DeleteFile|2|  
|RenameFile|3|  
|SetAttributes|4|  
|CreateDirectory|5|  
|CopyDirectory|6|  
|MoveDirectory|7|  
|DeleteDirectory|8|  
|DeleteDirectoryContent|9|  
  
 `Attributes` プロパティ-から値を使用して設定、`DTSFileSystemAttributes`列挙します。  
  
|DTSFileSystemAttributes の表示名|数値|  
|----------------------------------------------|-------------------|  
|標準|0|  
|Archive|1|  
|[非表示]|2|  
|ReadOnly|4|  
|システム|8|  
  
### <a name="ftp-task"></a>FTP タスク  
 `Operation` プロパティ-から値を使用して設定、`DTSFTPOp`列挙します。  
  
|DTSFTPOp の表示名|数値|  
|-------------------------------|-------------------|  
|Send|0|  
|Receive|1|  
|DeleteLocal|2|  
|DeleteRemote|3|  
|MakeDirLocal|4|  
|MakeDirRemote|5|  
|RemoveDirLocal|6|  
|RemoveDirRemote|7|  
  
### <a name="message-queue-task"></a>Message Queue Task  
 `MessageType` プロパティ-から値を使用して設定、`MQMessageType`列挙します。  
  
|MQMessageType の表示名|数値|  
|------------------------------------|-------------------|  
|DTSMQMessageType_String|0|  
|DTSMQMessageType_DataFile|1|  
|DTSMQMessageType_Variables|2|  
|DTSMQMessagType_StringMessageToVariable|3|  
  
 `StringCompareType` プロパティ-から値を使用して設定、`MQStringMessageCompare`列挙します。  
  
|MQStringMessageCompare の表示名|数値|  
|---------------------------------------------|-------------------|  
|DTSMQStringMessageCompare_None|0|  
|DTSMQStringMessageCompare_Exact|1|  
|DTSMQStringMessageCompare_IgnoreCase|2|  
|DTSMQStringMessageCompare_Contains|3|  
  
 `TaskType` プロパティ-から値を使用して設定、`MQType`列挙します。  
  
|MQType の表示名|数値|  
|-----------------------------|-------------------|  
|DTSMQType_Sender|0|  
|DTSMQType_Receiver|1|  
  
### <a name="send-mail-task"></a>メール送信タスク  
 `MessageSourceType` プロパティ-から値を使用して設定、`SendMailMessageSourceType`列挙します。  
  
|SendMailMessageSourceType の表示名|数値|  
|------------------------------------------------|-------------------|  
|DirectInput|0|  
|[FileConnection]|1|  
|変数|2|  
  
 `Priority` プロパティ-から値を使用して設定、`MailPriority`列挙します。  
  
|MailPriority の表示名|数値|  
|-----------------------------------|-------------------|  
|高|1|  
|標準|3|  
|Low|5|  
  
### <a name="transfer-database-task"></a>データベース転送タスク  
 `Action` プロパティ-から値を使用して設定、`TransferAction`列挙します。  
  
|TransferAction の表示名|数値|  
|-------------------------------------|-------------------|  
|[コピー]|0|  
|[詳細ビュー]|1|  
  
 `Method` プロパティ-から値を使用して設定、`TransferMethod`列挙します。  
  
|TransferMethod の表示名|数値|  
|-------------------------------------|-------------------|  
|DatabaseOffline|0|  
|DatabaseOnline|1|  
  
### <a name="transfer-error-messages-task"></a>エラー メッセージ転送タスク  
 `IfObjectExists` プロパティ-から値を使用して設定、`IfObjectExists`列挙します。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-jobs-task"></a>ジョブ転送タスク  
 `IfObjectExists` プロパティ-から値を使用して設定、`IfObjectExists`列挙します。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-logins-task"></a>ログイン転送タスク  
 `IfObjectExists` プロパティ-から値を使用して設定、`IfObjectExists`列挙します。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
 `LoginsToTransfer` プロパティ-から値を使用して設定、`LoginsToTransfer`列挙します。  
  
|LoginsToTransfer の表示名|数値|  
|---------------------------------------|-------------------|  
|[AllLogins]|0|  
|[SelectedLogins]|1|  
|[AllLoginsFromSelectedDatabases]|2|  
  
### <a name="transfer-master-stored-procedures-task"></a>Master ストアド プロシージャ転送タスク  
 `IfObjectExists` プロパティ-から値を使用して設定、`IfObjectExists`列挙します。  
  
|IfObjectExists の表示名|数値|  
|-------------------------------------|-------------------|  
|[FailTask]|0|  
|Overwrite|1|  
|Skip|2|  
  
### <a name="transfer-sql-server-objects-task"></a>SQL Server オブジェクトの転送タスク  
 `ExistingData` プロパティ-から値を使用して設定、`ExistingData`列挙します。  
  
|ExistingData の表示名|数値|  
|-----------------------------------|-------------------|  
|[置換]|0|  
|追加|1|  
  
### <a name="web-service-task"></a>Web サービス タスク  
 `OutputType` プロパティ-から値を使用して設定、`DTSOutputType`列挙します。  
  
|DTSOutputType の表示名|数値|  
|------------------------------------|-------------------|  
|ファイル|0|  
|変数|1|  
  
### <a name="wmi-data-reader-task"></a>WMI データ リーダー タスク  
 `OverwriteDestination` プロパティ-から値を使用して設定、`OverwriteDestination`列挙します。  
  
|OverwriteDestination の表示名|数値|  
|-------------------------------------------|-------------------|  
|OverwriteDestination|0|  
|AppendToDestination|1|  
|KeepOriginal|2|  
  
 `OutputType` プロパティ-から値を使用して設定、`OutputType`列挙します。  
  
|OutputType の表示名|数値|  
|---------------------------------|-------------------|  
|DataTable|0|  
|PropertyValue|1|  
|PropertyNameAndValue|2|  
  
 `DestinationType` プロパティ-から値を使用して設定、`DestinationType`列挙します。  
  
|DestinationType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
  
 `WqlQuerySourceType` プロパティ-から値を使用して設定、`QuerySourceType`列挙します。  
  
|QuerySourceType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|DirectInput|1|  
|変数|2|  
  
 WMI イベント監視の `ActionAtEvent` プロパティ - `ActionAtEvent` 列挙子からの値を使用して設定します。  
  
|ActionAtEvent の表示名|数値|  
|------------------------------------|-------------------|  
|LogTheEventAndFireDTSEvent|0|  
|LogTheEvent|1|  
  
 `ActionAtTimeout` プロパティ-から値を使用して設定、`ActionAtTimeout`列挙します。  
  
|ActionAtTimeout の表示名|数値|  
|--------------------------------------|-------------------|  
|LogTimeoutAndFireDTSEvent|0|  
|LogTimeout|1|  
  
 `AfterEvent` プロパティ-から値を使用して設定、`AfterEvent`列挙します。  
  
|AfterEvent の表示名|数値|  
|---------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `AfterTimeout` プロパティ-から値を使用して設定、`AfterTimeout`列挙します。  
  
|AfterTimeout の表示名|数値|  
|-----------------------------------|-------------------|  
|ReturnWithSuccess|0|  
|ReturnWithFailure|1|  
|WatchfortheEventAgain|2|  
  
 `WqlQuerySourceType` プロパティ-から値を使用して設定、`QuerySourceType`列挙します。  
  
|QuerySourceType の表示名|数値|  
|--------------------------------------|-------------------|  
|[FileConnection]|0|  
|DirectInput|1|  
|変数|2|  
  
### <a name="xml-task"></a>XML タスク  
 `OperationType` プロパティ-から値を使用して設定、`DTSXMLOperation`列挙します。  
  
|DTSXMLOperation の表示名|数値|  
|--------------------------------------|-------------------|  
|[検証]|0|  
|XSLT (XSLT)|1|  
|[XPath]|2|  
|Merge|3|  
|[Diff]|4|  
|[Patch]|5|  
  
 `SourceType`、`SecondOperandType`、および `XPathSourceType` の各プロパティ - `DTSXMLSourceType` 列挙子からの値を使用して設定します。  
  
|DTSXMLSourceType の表示名|数値|  
|---------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
|DirectInput|2|  
  
 `DestinationType` および**DiffGramDestinationType**プロパティ — から値を使用して設定、`DTSXMLSaveResultTo`列挙します。  
  
|DTSXMLSaveResultTo の表示名|数値|  
|-----------------------------------------|-------------------|  
|[FileConnection]|0|  
|変数|1|  
  
 `ValidationType` プロパティ-から値を使用して設定、`DTSXMLValidationType`列挙します。  
  
|DTSXMLValidationType の表示名|数値|  
|-------------------------------------------|-------------------|  
|[DTD]|0|  
|[XSD]|1|  
  
 `XPathOperation` プロパティ-から値を使用して設定、`DTSXMLXPathOperation`列挙します。  
  
|DTSXMLXPathOperation の表示名|数値|  
|-------------------------------------------|-------------------|  
|Evaluation|0|  
|値|1|  
|NodeList|2|  
  
 `DiffOptions` プロパティ-から値を使用して設定、`DTSXMLDiffOptions`列挙します。 この列挙子の各オプションは相互排他的ではなく、複数を同時に指定することができます。 複数のオプションを使用するには、適用するオプションをコンマ区切りのリストで指定します。  
  
|DTSXMLDiffOptions の表示名|数値|  
|----------------------------------------|-------------------|  
|なし|0|  
|IgnoreChildOrder|1|  
|[IgnoreComments]|2|  
|IgnorePI|4|  
|IgnoreWhitespace|8|  
|[IgnoreNamespaces]|16|  
|[IgnorePrefixes]|32|  
|IgnoreXmlDecl|64|  
|IgnoreDtd|128|  
  
 `DiffAlgorithm` プロパティ-から値を使用して設定、`DTSXMLDiffAlgorithm`列挙します。  
  
|DTSXMLDiffAlgorithm の表示名|数値|  
|------------------------------------------|-------------------|  
|Auto|0|  
|[高速]|1|  
|[詳細]|2|  
  
##  <a name="MaintenancePlanTasks"></a> メンテナンス プランのタスク  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、メンテナンス プランおよび [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ用の SQL Server タスクを実行する一連のタスクが含まれています。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、プログラムによるこれらのタスクの操作がサポートされていません。また、プログラミング リファレンス ドキュメントには、これらのタスクとその列挙子に関する API ドキュメントが含まれていません。  
  
### <a name="all-maintenance-tasks"></a>すべてのメンテナンス タスク  
 すべてのメンテナンス タスクでは、次の列挙子を使用して、指定したプロパティを設定します。  
  
 `DatabaseSelectionType` プロパティ-から値を使用して設定、`DatabaseSelection`列挙します。  
  
|DatabaseSelection の表示名|数値|  
|----------------------------------------|-------------------|  
|なし|0|  
|All|1|  
|システム|2|  
|ユーザー|3|  
|Specific|4|  
  
 `TableSelectionType` プロパティ-から値を使用して設定、`TableSelection`列挙します。  
  
|TableSelection の表示名|数値|  
|-------------------------------------|-------------------|  
|なし|0|  
|All|1|  
|Specific|2|  
  
 `ObjectTypeSelection` プロパティ-から値を使用して設定、`ObjectType`列挙します。  
  
|ObjectType の表示名|数値|  
|---------------------------------|-------------------|  
|テーブル|0|  
|表示|1|  
|TableView|2|  
  
### <a name="back-up-database-task"></a>データベースのバックアップ タスク  
 `DestinationCreationType` プロパティ-から値を使用して設定、`DestinationType`列挙します。  
  
|DestinationType の表示名|数値|  
|--------------------------------------|-------------------|  
|Auto|0|  
|手動|1|  
  
 `ExistingBackupsAction` プロパティ-から値を使用して設定、`ActionForExistingBackups`列挙します。  
  
|ActionForExistingBackups の表示名|数値|  
|-----------------------------------------------|-------------------|  
|追加|0|  
|Overwrite|1|  
  
 `BackupAction` プロパティ-から値を使用して設定、`BackupTaskType`列挙します。 このプロパティが連動、`BackupIsIncremental`タスクが実行されるバックアップの種類を定義するプロパティです。  
  
|BackupTaskType の表示名|数値|  
|-------------------------------------|-------------------|  
|[データベース]|0|  
|[ファイル]|1|  
|Log|2|  
  
 `BackupDevice` プロパティ - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の `DeviceType` 列挙子からの値を使用して設定します。  
  
|DeviceType の表示名|数値|  
|---------------------------------|-------------------|  
|LogicalDevice|0|  
|Tape|1|  
|ファイル|2|  
|Pipe|3|  
|VirtualDevice|4|  
  
### <a name="maintenance-cleanup-task"></a>メンテナンス クリーンアップ タスク  
 `FileTypeSelected` プロパティ-から値を使用して設定、`FileType`列挙します。  
  
|FileType の表示名|数値|  
|-------------------------------|-------------------|  
|FileBackup|0|  
|FileReport|1|  
  
 `OlderThanTimeUnitType` プロパティ-から値を使用して設定、`TimeUnitType`列挙します。  
  
|TimeUnitType の表示名|数値|  
|-----------------------------------|-------------------|  
|日|0|  
|Week|1|  
|Month|2|  
|年|3|  
  
### <a name="update-statistics-task"></a>統計の更新タスク  
 `UpdateType` プロパティ - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) の `StatisticsTarget` 列挙子からの値を使用して設定します。  
  
|StatisticsTarget の表示名|数値|  
|---------------------------------------|-------------------|  
|[列]|1|  
|インデックス|2|  
|All|3|  
  
##  <a name="CommonProperties"></a> 共通プロパティ  
 パッケージ、タスク、Foreach ループ コンテナー、For ループ コンテナー、およびシーケンス コンテナーでは、次の列挙子を使用して、指定されたプロパティを設定できます。  
  
 `ForceExecutionResult` プロパティ-から値を使用して設定、`DTSForcedExecResult`列挙します。  
  
|DTSForcedExecResult の表示名|数値|  
|------------------------------------------|-------------------|  
|なし|-1|  
|成功|0|  
|失敗|1|  
|Completion|2|  
  
 `IsolationLevel` プロパティ - .NET Framework の `IsolationLevel` 列挙子で設定します。 詳細については、 [MSDN ライブラリ](http://go.microsoft.com/fwlink?LinkId=17313)の .NET Framework クラス ライブラリを参照してください。  
  
 `LoggingMode` プロパティ-から値を使用して設定、`DTSLoggingMode`列挙します。  
  
|DTSLoggingMode の表示名|数値|  
|-------------------------------------|-------------------|  
|UseParentSetting|0|  
|有効|1|  
|Disabled|2|  
  
 `TransactionOption` プロパティ-から値を使用して設定、`DTSTransactionOption`列挙します。  
  
|DTSTransactionOption の表示名|数値|  
|-------------------------------------------|-------------------|  
|NotSupported|0|  
|Supported|1|  
|必須|2|  
  
## <a name="related-tasks"></a>Related Tasks  
 [プロパティ式を追加または変更する](add-or-change-a-property-expression.md)  
  
## <a name="see-also"></a>参照  
 [パッケージのプロパティ式を使用します。](use-property-expressions-in-packages.md)   
 [Integration Services &#40;SSIS&#41;パッケージ](../integration-services-ssis-packages.md)   
 [Integration Services コンテナー](../control-flow/integration-services-containers.md)   
 [Integration Services タスク](../control-flow/integration-services-tasks.md)   
 [優先順位制約](../control-flow/precedence-constraints.md)  
  
  