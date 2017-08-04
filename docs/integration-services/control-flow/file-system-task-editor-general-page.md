---
title: "ファイル システム タスク エディター (全般 ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab4f38b627ab6fdc566e9ba452d3bf83f9630bb9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="file-system-task-editor-general-page"></a>[ファイル システム タスク エディター] ([全般] ページ)
  **[ファイル システム タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクで実行するファイル システム操作を構成できます。  
  
 このタスクの詳細については、「 [File System Task](../../integration-services/control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。  
  
 SourceConnection プロパティと DestinationConnection プロパティを設定して、ソースとターゲットの接続マネージャーを指定する必要があります。 タスクでソースまたはターゲットとして使用されるファイルを指すファイル接続マネージャーの名前を指定することも、ファイルのパスが変数に格納されていれば変数の名前を指定することもできます。 変数を使用してファイル パスを保存するには、最初に、IsSourcePathVariable オプション (ソース接続) および IsDestinationPatheVariable オプション (ターゲット接続) を **True**に設定しておく必要があります。 その後で、既存のシステム変数またはユーザー定義変数を選択するか、新しい変数を作成できます。 変数のスコープは、 **[変数の追加]** ダイアログ ボックスで構成および指定できます。 スコープは、ファイル システム タスクまたは親コンテナーにする必要があります。 詳細については、「[Integration Services (SSIS) Variables](../../integration-services/integration-services-ssis-variables.md)」(Integration Services (SSIS) の変数) と「[Use Variables in Packages](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)」(パッケージで変数を使用する) を参照してください。  
  
> [!NOTE]  
>  **SourceConnection** プロパティと **DestinationConnection** プロパティに選択した変数をオーバーライドするには、**Source** プロパティと **Destination** プロパティに式を入力します。 式は、 **ファイル システム タスク エディター** の **[式]**ページで入力します。 たとえば、タスクで変換先として使用するファイルのパスを設定するには、特定の状況下では変数 A、別の状況下では変数 B を使用することがあります。  
  
> [!NOTE]  
>  ファイル システム タスクは、1 つのファイルまたはディレクトリのみを処理できます。 したがって、このタスクでは、ワイルドカード文字を使用して複数のファイルまたはディレクトリに同じ処理を行うことはできません。 ファイル システム タスクが複数のファイルやディレクトリに対して同じ処理を繰り返し行うようにするには、ファイル システム タスクを Foreach ループ コンテナー内に配置します。 詳細については、「 [File System Task](../../integration-services/control-flow/file-system-task.md)」(ファイル システム タスク) を参照してください。  
  
 さまざまな変数を使用する式を使用できます。  
  
## <a name="options"></a>オプション  
 **[IsDestinationPathVariable]**  
 対象になるパスを変数に格納するかどうかを示します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプション **[DestinationVariable]**が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプション **[DestinationConnection]**が表示されます。|  
  
 **[OverwriteDestination]**  
 操作によって対象になるディレクトリ内のファイルを上書きできるかどうかを指定します。  
  
 **名前**  
 ファイル システム タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **Description**  
 ファイル システム タスクの説明を入力します。  
  
 **操作**  
 実行するファイル システム操作を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**ディレクトリのコピー**|ディレクトリをコピーします。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ファイルのコピー**|ファイルをコピーします。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ディレクトリの作成**|ディレクトリを作成します。 この値を選択すると、ソース ディレクトリとターゲット ディレクトリを指定するための動的オプションが表示されます。|  
|**ディレクトリの削除**|ディレクトリを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ディレクトリ コンテンツの削除**|ディレクトリのコンテンツを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ファイルの削除**|ファイルを削除します。 この値を選択すると、ソースを指定するための動的オプションが表示されます。|  
|**ディレクトリの移動**|ディレクトリを移動します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。|  
|**ファイルの移動**|ファイルを移動します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。 ファイルを移動するときは、移動先として指定するディレクトリ パスにファイル名を含めないようにします。|  
|**ファイル名の変更**|ファイルの名前を変更します。 この値を選択すると、ソースとターゲットを指定するための動的オプションが表示されます。 ファイル名を変更するときは、変更先として指定するディレクトリ パスに新しいファイル名を含めます。|  
|**属性の設定**|ファイルまたはディレクトリの属性を設定します。 この値を選択すると、ソースと操作を指定するための動的オプションが表示されます。|  
  
 **[IsSourcePathVariable]**  
 対象になるパスを変数に格納するかどうかを示します。 このプロパティのオプションを次の表に示します。  
  
|値||  
|-----------|-|  
|**True**|対象になるパスは変数に格納されます。 この値を選択すると、動的オプション **[SourceVariable]**が表示されます。|  
|**False**|対象になるパスは、ファイル接続マネージャーで指定されます。 この値を選択すると、動的オプション **[DestinationVariable]**が表示されます。|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>[IsDestinationPathVariable] の動的オプション  
  
### <a name="isdestinationpathvariable--true"></a>[IsDestinationPathVariable] = [True]  
 **[DestinationVariable]**  
 一覧で、変数名を選択するかクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="isdestinationpathvariable--false"></a>[IsDestinationPathVariable] = [False]  
 **DestinationConnection**  
 一覧で、ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>[IsSourcePathVariable] の動的オプション  
  
### <a name="issourcepathvariable--true"></a>[IsSourcePathVariable] = [True]  
 **[SourceVariable]**  
 一覧で、変数名を選択するかクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="issourcepathvariable--false"></a>[IsSourcePathVariable] = [False]  
 **SourceConnection**  
 一覧で、ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
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
 **UseDirectoryIfExists**  
 **[ディレクトリの作成]** 操作で、新しいディレクトリを作成せずに、指定された名前の既存のディレクトリを使用するかどうかを指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
  
