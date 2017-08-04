---
title: "XML タスク エディター (全般 ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f9dc1f49a7e2fcee8b87546585075d016f1f6ace
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="xml-task-editor-general-page"></a>XML Task Editor (General Page)
  **[XML タスク エディター]** ダイアログ ボックスの **[全般]** ノードを使用すると、操作の種類を指定したり構成したりできます。  
  
 このタスクの詳細については、「 [XML タスク](../../integration-services/control-flow/xml-task.md) 」および「 [XML タスクを使った XML の検証](../../integration-services/control-flow/validate-xml-with-the-xml-task.md)」をご覧ください。 XML ドキュメントとデータの操作の詳細については、MSDN ライブラリの「[.NET Framework における XML の使用](http://go.microsoft.com/fwlink/?LinkId=56214)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[OperationType]**  
 一覧から操作の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[検証]**|文書型定義 (DTD) または XML スキーマ定義 (XSD) スキーマに対して XML ドキュメントを検証します。 このオプションを選択すると、 **[Validate]**セクションに動的オプションが表示されます。|  
|**XSLT (XSLT)**|XML ドキュメントに対して XSL 変換を実行します。 このオプションを選択すると、 **[XSLT]**セクションに動的オプションが表示されます。|  
|**[XPath]**|XPath クエリと評価を実行します。 このオプションを選択すると、 **[Xpath]**セクションに動的オプションが表示されます。|  
|**Merge**|2 つの XML ドキュメントをマージします。 このオプションを選択すると、 **[Merge]**セクションに動的オプションが表示されます。|  
|**[Diff]**|2 つの XML ドキュメントを比較します。 このオプションを選択すると、 **[Diff]**セクションに動的オプションが表示されます。|  
|**[Patch]**|Diff 操作からの出力を適用して、新しいドキュメントを作成します。 このオプションを選択すると、 **[Patch]**セクションに動的オプションが表示されます。|  
  
 **[SourceType]**  
 XML ドキュメントのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **ソース**  
 **[ソース]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**ソース**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**ソース**に設定されている**変数**を既存の変数を選択するかをクリックして**\<新しい変数… >**新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="operationtype-dynamic-options"></a>[OperationType] の動的オプション  
  
### <a name="operationtype--validate"></a>[OperationType] = [Validate]  
 Validate 操作用のオプションを指定します。  
  
 **[SaveOperationResult]**  
 XML タスクが Validate 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 既存のファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[ValidationType]**  
 検証の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[DTD]**|文書型定義 (DTD) を使用します。|  
|**[XSD]**|XML スキーマ定義 (XSD) スキーマを使用します。 このオプションを選択すると、 **[ValidationType]**セクションに動的オプションが表示されます。|  
  
 **[FailOnValidationFail]**  
 ドキュメントの検証に失敗した場合に、操作が失敗するかどうかを指定します。  
  
 **[ValidationDetails]**  
 このプロパティの値が true の場合は、詳細なエラー出力を表示します。 詳細については、「 [Validate XML with the XML Task](../../integration-services/control-flow/validate-xml-with-the-xml-task.md)」を参照してください。  
  
### <a name="validationtype-dynamic-options"></a>[ValidationType] の動的オプション  
  
#### <a name="validationtype--xsd"></a>[ValidationType] = [XSD]  
 **[SecondOperandType]**  
 2 番目の XML ドキュメントのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**XPathStringSourceType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="operationtype--xslt"></a>[OperationType] = [XSLT]  
 XSLT 操作用のオプションを指定します。  
  
 **[SaveOperationResult]**  
 XML タスクが XSLT 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 場合**DestinationType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**DestinationType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperandType]**  
 2 番目の XML ドキュメントのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**XPathStringSourceType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="operationtype--xpath"></a>[OperationType] = [XPath]  
 XPath 操作用のオプションを指定します。  
  
 **[SaveOperationResult]**  
 XML タスクが XPath 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 場合**DestinationType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**DestinationType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperandType]**  
 2 番目の XML ドキュメントのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**XPathStringSourceType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[PutResultInOneNode]**  
 結果を 1 つのノードに記述するかどうかを指定します。  
  
 **[XPathOperation]**  
 XPath の結果の種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**Evaluation**|XPath 関数の結果を返します。|  
|**[ノード リスト]**|選択されたノードを XML フラグメントとして返します。|  
|**値**|文字列に連結された、選択されたすべてのノードの内部テキスト値を返します。|  
  
### <a name="operationtype--merge"></a>[OperationType] = [Merge]  
 Merge 操作用のオプションを指定します。  
  
 **[XPathStringSourceType]**  
 XML ドキュメントのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[XPathStringSource]**  
 **[XPathStringSourceType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**XPathStringSourceType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**XPathStringSourceType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 XPath ステートメントを使用してソース ドキュメント内でのマージ場所を特定すると、このステートメントによって 1 つのノードが返されます。 ステートメントによって複数のノードが返された場合は、最初のノードだけが使用されます。 2 番目のドキュメントの内容は、XPath クエリによって返される最初のノードでマージされます。  
  
 **[SaveOperationResult]**  
 XML タスクが Merge 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 場合**DestinationType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**DestinationType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperandType]**  
 2 番目の XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**SecondOperandType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="operationtype--diff"></a>[OperationType] = [Diff]  
 Diff 操作用のオプションを指定します。  
  
 **[DiffAlgorithm]**  
 Diff アルゴリズムを選択して、文書を比較する場合に使用します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**Auto**|XML タスクに、高速アルゴリズムを使用するか、詳細アルゴリズムを使用するかを決定します。|  
|**[高速]**|高速ではあるが詳細ではない Diff アルゴリズムを使用します。|  
|**[詳細]**|詳細な Diff アルゴリズムを使用します。|  
  
 **[DiffOptions]**  
 Diff 操作に適用するための Diff オプションを設定します。 次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**[IgnoreXMLDeclaration]**|XML 宣言を比較するかどうかを指定します。|  
|**[IgnoreDTD]**|文書型定義 (DTD) を無視するかどうかを指定します。|  
|**[IgnoreWhiteSpaces]**|ドキュメントを比較するときに空白の量の違いを無視するかどうかを指定します。|  
|**[IgnoreNamespaces]**|要素名および属性名の名前空間の URI (Uniform Resource Identifier) を比較するかどうかを指定します。<br /><br /> 注: このオプションが **True**に設定されている場合、ローカル名が同じで、名前空間が異なる 2 つの要素は同一と見なされます。|  
|**[IgnoreProcessingInstructions]**|処理命令を比較するかどうかを指定します。|  
|**[IgnoreOrderOfChildElements]**|子の要素の順序を比較するかどうかを指定します。<br /><br /> 注: このオプションが **True**に設定されている場合、兄弟の一覧で位置のみが異なる子要素は同一と見なされます。|  
|**[IgnoreComments]**|コメント ノードを比較するかどうかを指定します。|  
|**[IgnorePrefixes]**|要素名および属性名のプレフィックスを比較するかどうかを指定します。<br /><br /> 注: このオプションが **True**に設定されている場合、ローカル名が同じで、名前空間 URI とプレフィックスが異なる 2 つの要素は同一と見なされます。|  
  
 **[FailOnDifference]**  
 Diff 操作が失敗した場合に、タスクが失敗するかどうかを指定します。  
  
 **[SaveDiffGram]**  
 比較結果である DiffGram ドキュメントを保存するかどうかを指定します。  
  
 **[SaveOperationResult]**  
 XML タスクが Diff 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 場合**DestinationType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**DestinationType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperandType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**SecondOperandType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="operationtype--patch"></a>[OperationType] = [Patch]  
 Patch 操作用のオプションを指定します。  
  
 **[SaveOperationResult]**  
 XML タスクが Patch 操作の出力を保存するかどうかを指定します。  
  
 **[OverwriteDestination]**  
 対象となるファイルまたは変数を上書きするかどうかを指定します。  
  
 **変換先**  
 場合**DestinationType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**DestinationType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[DestinationType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperandType]**  
 XML ドキュメントの対象となる種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを XML ドキュメントに設定します。|  
|**[ファイル接続]**|XML ドキュメントが含まれているファイルを選択します。|  
|**変数**|ソースを XML ドキュメントが含まれている変数に設定します。|  
  
 **[SecondOperand]**  
 **[SecondOperandType]** が **[直接入力]**に設定されている場合は、XML コードを指定するか、省略記号ボタン **([...])** をクリックしてから **[ドキュメント ソース エディター]** ダイアログ ボックスを使用して XML を指定します。  
  
 場合**SecondOperandType**に設定されている**ファイルの接続**をファイル接続マネージャーを選択するかをクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 場合**SecondOperandType**に設定されている**変数**を既存の変数を選択するかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
  
