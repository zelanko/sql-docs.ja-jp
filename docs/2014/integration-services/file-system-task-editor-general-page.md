---
title: '[ファイルシステムタスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 342a718e1d72a257e469cd855ffd60fff6c5704d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425679"
---
# <a name="file-system-task-editor-general-page"></a>[ファイル システム タスク エディター] \([全般] ページ)
  **[ファイル システム タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクで実行するファイル システム操作を構成できます。  
  
 このタスクの詳細については、「 [File System Task](control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。  
  
 SourceConnection プロパティと DestinationConnection プロパティを設定して、ソースとターゲットの接続マネージャーを指定する必要があります。 タスクでソースまたはターゲットとして使用されるファイルを指すファイル接続マネージャーの名前を指定することも、ファイルのパスが変数に格納されていれば変数の名前を指定することもできます。 変数を使用してファイル パスを保存するには、最初に、IsSourcePathVariable オプション (ソース接続) および IsDestinationPatheVariable オプション (ターゲット接続) を **True**に設定しておく必要があります。 その後で、既存のシステム変数またはユーザー定義変数を選択するか、新しい変数を作成できます。 変数のスコープは、 **[変数の追加]** ダイアログ ボックスで構成および指定できます。 スコープは、ファイル システム タスクまたは親コンテナーにする必要があります。 詳細については、「 [Integration Services &#40;SSIS&#41; 変数](integration-services-ssis-variables.md)」および「[パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)」を参照してください。  
  
> [!NOTE]  
>  プロパティとプロパティに対して選択した変数をオーバーライドするには、 `SourceConnection` `DestinationConnection` **Source**プロパティと**Destination**プロパティに式を入力します。 式は、 **ファイル システム タスク エディター** の **[式]** ページで入力します。 たとえば、タスクで変換先として使用するファイルのパスを設定するには、特定の状況下では変数 A、別の状況下では変数 B を使用することがあります。  
  
> [!NOTE]  
>  ファイル システム タスクは、1 つのファイルまたはディレクトリのみを処理できます。 したがって、このタスクでは、ワイルドカード文字を使用して複数のファイルまたはディレクトリに同じ処理を行うことはできません。 ファイル システム タスクが複数のファイルやディレクトリに対して同じ処理を繰り返し行うようにするには、ファイル システム タスクを Foreach ループ コンテナー内に配置します。 詳細については、「 [File System Task](control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。  
  
 さまざまな変数を使用する式を使用できます。  
  
## <a name="options"></a>オプション  
 **[IsDestinationPathVariable]**  
 対象になるパスを変数に格納するかどうかを示します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**True**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプション **[DestinationVariable]** が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプションの [] が表示され `DestinationConnection` ます。|  
  
 **[OverwriteDestination]**  
 操作によって対象になるディレクトリ内のファイルを上書きできるかどうかを指定します。  
  
 **名前**  
 ファイル システム タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **説明**  
 ファイル システム タスクの説明を入力します。  
  
 **操作**  
 実行するファイル システム操作を選択します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**ディレクトリのコピー**|ディレクトリをコピーします。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ファイルのコピー**|ファイルのコピー この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ディレクトリの作成**|ディレクトリを作成します。 この値を選択すると、ソース ディレクトリとターゲット ディレクトリを指定するための動的オプションが表示されます。|  
|**ディレクトリの削除**|ディレクトリを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ディレクトリ コンテンツの削除**|ディレクトリのコンテンツを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ファイルの削除**|ファイルを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ディレクトリの移動**|ディレクトリを移動します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ファイルの移動**|ファイルを移動します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。<br /><br /> 注: ファイルを移動する場合は、保存先として指定するディレクトリパスにファイル名を含めないでください。|  
|**ファイル名の変更**|ファイルの名前を変更します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。<br /><br /> 注: ファイルの名前を変更する場合は、変換先に指定するディレクトリパスに新しいファイル名を含めます。|  
|**属性の設定**|ファイルまたはディレクトリの属性を設定します。 この値を選択すると、ソースと操作を指定するための動的オプションが表示されます。|  
  
 `IsSourcePathVariable`  
 対象になるパスを変数に格納するかどうかを示します。 このプロパティのオプションを次の表に示します。  
  
|[値]||  
|-----------|-|  
|**本来**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプション **[SourceVariable]** が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプション **[DestinationVariable]** が表示されます。|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>[IsDestinationPathVariable] の動的オプション  
  
### <a name="isdestinationpathvariable--true"></a>[IsDestinationPathVariable] = [True]  
 **[DestinationVariable]**  
 一覧から変数名を選択するか、をクリックして \<**New variable...**> 新しい変数を作成します。  
  
 **関連トピック:** [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
### <a name="isdestinationpathvariable--false"></a>[IsDestinationPathVariable] = [False]  
 `DestinationConnection`  
 ファイル接続マネージャーを一覧から選択するか、をクリックして \<**New connection...**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、 [ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>[IsSourcePathVariable] の動的オプション  
  
### <a name="issourcepathvariable--true"></a>[IsSourcePathVariable] = [True]  
 **[SourceVariable]**  
 一覧から変数名を選択するか、をクリックして \<**New variable...**> 新しい変数を作成します。  
  
 **関連トピック:** [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)  
  
### <a name="issourcepathvariable--false"></a>[IsSourcePathVariable] = [False]  
 `SourceConnection`  
 ファイル接続マネージャーを一覧から選択するか、をクリックして \<**New connection...**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、 [ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="operation-dynamic-options"></a>[Operation] の動的オプション  
  
### <a name="operation--set-attributes"></a>[Operation] = [属性の設定]  
 **[非表示]**  
 ファイルまたはディレクトリを表示するかどうかを示します。  
  
 **ReadOnly**  
 ファイルが読み取り専用かどうかを示します。  
  
 **Archive**  
 ファイルまたはディレクトリをアーカイブするかどうかを示します。  
  
 **システム**  
 ファイルがオペレーティング システム ファイルかどうかを示します。  
  
### <a name="operation--create-directory"></a>[Operation] = [ディレクトリの作成]  
 `UseDirectoryIfExists`  
 **[ディレクトリの作成]** 操作で、新しいディレクトリを作成せずに、指定された名前の既存のディレクトリを使用するかどうかを指定します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
