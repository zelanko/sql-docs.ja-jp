---
title: パッケージのプロパティを設定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- checkpoints [Integration Services]
- execution properties [Integration Services]
- packages [Integration Services], properties
- identification properties [Integration Services]
- passwords [Integration Services]
- SSIS packages, properties
- transaction properties [Integration Services]
- updating package properties
- forced execution value properties [Integration Services]
- security properties [Integration Services]
- version properties [Integration Services]
- SQL Server Integration Services packages, properties
ms.assetid: 13f81c3e-2b18-4f83-b445-a2f4a2c560aa
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 12e500402c68da2e38fd88c5d061644a7f51fd58
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104852"
---
# <a name="set-package-properties"></a>パッケージのプロパティを設定する
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のグラフィカル インターフェイスを使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のパッケージを作成する場合、パッケージ オブジェクトのプロパティは [プロパティ] ウィンドウで設定します。  
  
 **[プロパティ]** ウィンドウでは、プロパティが分類され、アルファベット順で一覧が提供されます。 **[プロパティ]** ウィンドウの表示をカテゴリ別に並べ替えるには、[項目別] アイコンをクリックします。  
  
 カテゴリ別に並べ替えると、 **[プロパティ]** ウィンドウは、プロパティを次のカテゴリにグループ化します。  
  
-   [チェックポイント](#Checkpoints)  
  
-   [実行](#Execution)  
  
-   [強制実行値](#ForcedExecutionValue)  
  
-   [[識別]](#Identification)  
  
-   [その他](#Misc)  
  
-   [Security](#Security)  
  
-   [トランザクション](#Transactions)  
  
-   [バージョン](#Version)  
  
 **[プロパティ]** ウィンドウで設定できないパッケージの追加プロパティの詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.Package>」を参照してください。  
  
### <a name="to-set-package-properties-in-the-properties-window"></a>[プロパティ] ウィンドウでパッケージのプロパティを設定するには  
  
-   [パッケージのプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-package.md)  
  
## <a name="properties-by-category"></a>カテゴリ別プロパティ  
 次の表は、パッケージのプロパティをカテゴリ別に一覧表示しています。  
  
###  <a name="Checkpoints"></a> チェックポイント  
 このカテゴリのプロパティを使用すると、パッケージ制御フローで障害が発生した時点からパッケージを再開できます。制御フローの最初からパッケージを再実行する必要はありません。 詳細については、「 [チェックポイントを使用してパッケージを再開する](packages/restart-packages-by-using-checkpoints.md)」を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`CheckpointFileName`|パッケージを再開するチェックポイントに関する情報をキャプチャする、ファイルの名前です。 パッケージが正常に完了すると、このファイルは削除されます。|  
|`CheckpointUsage`|パッケージが再開できる時点を指定します。 値は、 `Never`、 `IfExists`、および`Always`します。 このプロパティの既定値は`Never`パッケージを再起動できないことを示します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSCheckpointUsage> 」を参照してください。|  
|`SaveCheckpoints`|パッケージの実行時にチェックポイントをチェックポイント ファイルに書き込むかどうかを指定します。 このプロパティの既定値は`False`します。|  
  
> [!NOTE]  
>  dtexec の `/CheckPointing on` オプションを使用すると、パッケージの `SaveCheckpoints` プロパティを True に設定した場合、および `CheckpointUsage` プロパティを Always に設定した場合と同等の効果が得られます。 詳しくは、「 [dtexec Utility](packages/dtexec-utility.md)」をご覧ください。  
  
###  <a name="Execution"></a> 実行  
 このカテゴリのプロパティは、パッケージ オブジェクトの実行時の動作を構成します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`DelayValidation`|パッケージの実行時までパッケージの検証を遅らせるかどうかを示します。 このプロパティの既定値は`False`します。|  
|**Disable**|パッケージを無効にするかどうかを示します。 このプロパティの既定値は`False`します。|  
|`DisableEventHandlers`|パッケージのイベント ハンドラーを実行するかどうかを示します。 このプロパティの既定値は`False`します。|  
|`FailPackageOnFailure`|パッケージ コンポーネント内でエラーが発生した場合、パッケージが失敗するかどうかを示します。 このプロパティの唯一の有効な値は`False`します。|  
|`FailParentOnError`|子コンテナーでエラーが発生した場合、親コンテナーが失敗するかどうかを示します。 このプロパティの既定値は `False` です。|  
|`MaxConcurrentExecutables`|パッケージが同時実行できる実行可能ファイルの数を示します。 このプロパティの既定値は **-1**です。これは、ファイル数に制限がないことを示します。|  
|`MaximumErrorCount`|パッケージが実行を停止するまでに発生が許可される、最大エラー数を示します。 このプロパティの既定値は **1**です。|  
|`PackagePriorityClass`|パッケージ スレッドの Win32 スレッド優先度クラスを示します。 値は、 `Default`、 `AboveNormal`、 `Normal`、 `BelowNormal`、`Idle`します。 このプロパティの既定値は`Default`します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSPriorityClass> 」を参照してください。|  
  
###  <a name="ForcedExecutionValue"></a> 強制実行値  
 このカテゴリのプロパティは、パッケージのオプションの実行値を構成します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`ForcedExecutionValue`|ForceExecutionValue に設定されている場合`True`パッケージが返すオプションの実行値を指定する値。 このプロパティの既定値は **0**です。|  
|`ForcedExecutionValueType`|ForcedExecutionValue のデータ型。 このプロパティの既定値は`Int32`します。|  
|`ForceExecutionValue`|コンテナーのオプションの実行値に特定の値を適用する必要があるかどうかを示すブール値です。 このプロパティの既定値は`False`します。|  
  
###  <a name="Identification"></a> [識別]  
 このカテゴリのプロパティは、パッケージの一意識別子や名前などの情報を提供します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`CreationDate`|パッケージが作成された日付です。|  
|`CreatorComputerName`|パッケージが作成されたコンピューターの名前です。|  
|`CreatorName`|パッケージの作成者の名前です。|  
|`Description`|パッケージ機能の説明です。|  
|`ID`|パッケージ GUID です。パッケージが作成されるときに割り当てられます。 このプロパティは読み取り専用です。 新しいランダムな値を生成する、`ID`プロパティで、  **\<Generate New ID >** ドロップダウン リストでします。|  
|`Name`|パッケージの名前です。|  
|`PackageType`|パッケージの種類です。 値は、 `Default`、 `DTSDesigner`、 `DTSDesigner100`、 `DTSWizard`、 `SQLDBMaint`、および`SQLReplication`します。 このプロパティの既定値は`Default`します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> 」を参照してください。|  
  
###  <a name="Misc"></a> その他  
 このカテゴリのプロパティは、パッケージで使用する構成と式にアクセスし、パッケージのロケールとログ モードに関する情報を提供するために使用されます。 詳細については、「 [パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md)」を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`Configurations`|パッケージで使用する構成のコレクションです。 パッケージ構成を表示して構成するには、参照ボタン ( **[...]** ) をクリックします。|  
|`Expressions`|パッケージのプロパティの式を作成するには、参照ボタン ( **[...]** ) をクリックします。<br /><br /> 注: オブジェクト モデルに含まれている [プロパティ] ウィンドウに表示されているプロパティだけでなくすべてのパッケージのプロパティのプロパティ式を作成することができます。<br /><br /> 詳細については、「 [パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md)」を参照してください。<br /><br /> 既存のプロパティの式を表示するには、`Expressions` を展開します。 式を変更したり評価するには、式テキスト ボックスの参照ボタン ( **[...]** ) をクリックします。|  
|`ForceExecutionResult`|パッケージの実行結果です。 値は、 `None`、 `Success`、 `Failure`、および`Completion`します。 このプロパティの既定値は`None`します。 詳細については、「T:Microsoft.SqlServer.Dts.Runtime.DTSForcedExecResult」を参照してください。|  
|`LocaleId`|Microsoft Win32 ロケールです。 このプロパティの既定値は、ローカル コンピューター上のオペレーティング システムのロケールです。|  
|`LoggingMode`|パッケージのログ記録の動作を指定する値です。 値は、 `Disabled`、 `Enabled`、および`UseParentSetting`します。 このプロパティの既定値は`UseParentSetting`します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 」を参照してください。|  
|`OfflineMode`|パッケージがオフライン モードかどうかを示します。 このプロパティは読み取り専用です。 プロジェクト レベルで設定されます。 通常、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーは、変換元と変換先に関連付けられたメタデータを検証するとき、パッケージで使用される各データ ソースに接続を試みます。 **[SSIS]** メニューの **[オフライン作業]** を有効にすると、パッケージを開く前でも、データ ソースを使用できないときに、接続を試行したり検証エラーが返されたりするのを防ぐことができます。 また、 **[オフライン作業]** を有効にしてデザイナーでの操作を高速化し、パッケージを検証するときだけこのオプションを無効にすることもできます。|  
|`SuppressConfigurationWarnings`|構成によって生成された警告を表示しないかどうかを示します。 このプロパティの既定値は`False`します。|  
|`UpdateObjects`|パッケージに含まれるオブジェクトの新しいバージョンが使用できるようになった場合に、パッケージを更新して、そのオブジェクトの新バージョンを使用するかどうかを示します。 たとえば、このプロパティに設定`True`、一括挿入タスクが含まれているパッケージが、新しいバージョンの一括挿入を使用するよう更新タスクを[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]を提供します。 このプロパティの既定値は`False`します。|  
  
###  <a name="Security"></a> セキュリティ  
 このカテゴリのプロパティを使用すると、パッケージの保護レベルが設定されます。 詳しくは、「 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)」をご覧ください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`PackagePassword`|パッケージの保護レベルのパスワード (`EncryptSensitiveWithPassword`と`EncryptAllWithPassword`) パスワードを必要とします。|  
|`ProtectionLevel`|パッケージの保護レベルです。 値は、 `DontSaveSensitive`、 `EncryptSensitiveWithUserKey`、 `EncryptSensitiveWithPassword`、 `EncryptAllWithPassword`、および**ServerStorage**します。 このプロパティの既定値は`EncryptSensitiveWithUserKey`します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel> 」を参照してください。|  
  
###  <a name="Transactions"></a> トランザクション  
 このカテゴリのプロパティは、パッケージの分離レベルとトランザクション オプションを構成します。 詳細については、「 [Integration Services のトランザクション](integration-services-transactions.md)」を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`IsolationLevel`|パッケージ トランザクションの分離レベルです。  このプロパティの既定値は`Serializable`します。 有効な値は <br />`Unspecified`<br />`Chaos`<br />`ReadUncommitted`<br />`ReadCommitted`<br />`RepeatableRead`<br />`Serializable`<br />`Snapshot`。<br /><br /> `IsolationLevel` プロパティは、`TransactionOption` プロパティの値が `Required` の場合にのみ、パッケージ トランザクションに適用されます。<br /><br /> 値、`IsolationLevel`次の条件に該当する場合、子コンテナーによって要求されたプロパティは無視されます。<br /><br /> 子コンテナーの `TransactionOption` プロパティの値が `Supported` である場合。<br />子コンテナーが親コンテナーのトランザクションに参加する場合。<br /><br /> コンテナーによって要求された `IsolationLevel` プロパティの値は、コンテナーが新しいトランザクションを開始する場合にのみ利用されます。 コンテナーは、次の場合に新しいトランザクションを開始します。<br /><br /> コンテナーの `TransactionOption` プロパティの値が `Required` である場合。<br />親がまだトランザクションを開始していない場合。<br /><br /> <br /><br /> 注:`Snapshot`の値、`IsolationLevel`プロパティは、パッケージ トランザクションと互換性がありません。 そのため、使用することはできません、`IsolationLevel`パッケージ トランザクションの分離レベルを設定するプロパティ`Shapshot`します。 代わりに、SQL クエリを使用して、パッケージ トランザクションに設定する`Snapshot`します。 詳細については、「[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)」を参照してください。<br /><br /> `IsolationLevel` プロパティの詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>」を参照してください。|  
|`TransactionOption`|パッケージに対するトランザクションの関与を示します。 値は、 `NotSupported`、 `Supported`、`Required`します。 このプロパティの既定値は`Supported`します。 詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption> 」を参照してください。|  
  
###  <a name="Version"></a> バージョン  
 このカテゴリのプロパティは、パッケージ オブジェクトのバージョンに関する情報を提供します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`VersionBuild`|パッケージのビルドのバージョン番号です。|  
|`VersionComments`|パッケージのバージョンに関するコメントです。|  
|`VersionGUID`|パッケージのバージョンの GUID です。 このプロパティは読み取り専用です。|  
|`VersionMajor`|パッケージの最新のメジャー バージョン。|  
|`VersionMinor`|パッケージの最新のマイナー バージョン。|  
  
  
