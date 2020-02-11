---
title: 共通プロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5b20a0d2f47e89070712a4063acba4da0225b85d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060962"
---
# <a name="common-properties"></a>共通プロパティ
  オブジェクトモデルのデータフローオブジェクト[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、コンポーネント、入力および出力、入力列、および出力列の各レベルで共通のプロパティとカスタムプロパティがあります。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 多くのプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
 ここでは、データ フロー オブジェクトの共通プロパティを一覧で示し、それぞれについて説明します。  
  
-   [Components](#components)  
  
-   [入力](#inputs)  
  
-   [入力列](#inputcolumns)  
  
-   [出力](#outputs)  
  
-   [出力列](#outputcolumns)  
  
 カスタム プロパティの詳細については、次のトピックを参照してください。  
  
-   [ADO NET カスタム プロパティ](data-flow/ado-net-custom-properties.md)  
  
-   [CDC 制御タスクのカスタム プロパティ](control-flow/cdc-control-task-custom-properties.md)  
  
-   [CDC ソースのカスタム プロパティ](data-flow/cdc-source-custom-properties.md)  
  
-   [データ マイニング モデル トレーニング変換先のカスタム プロパティ](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [DataReader 変換先のカスタム プロパティ](data-flow/datareader-destination-custom-properties.md)  
  
-   [ディメンション処理変換先のカスタム プロパティ](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Excel のカスタム プロパティ](data-flow/excel-custom-properties.md)  
  
-   [フラット ファイルのカスタム プロパティ](data-flow/flat-file-custom-properties.md)  
  
-   [ODBC 入力先のカスタム プロパティ](data-flow/odbc-destination-custom-properties.md)  
  
-   [ODBC 入力元のカスタム プロパティ](data-flow/odbc-source-custom-properties.md)  
  
-   [カスタムプロパティの OLE DB](data-flow/ole-db-custom-properties.md)カスタムプロパティの OLE DB  
  
-   [パーティション処理変換先のカスタム プロパティ](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [RAW ファイルのカスタム プロパティ](data-flow/raw-file-custom-properties.md)  
  
-   [レコードセット変換先のカスタム プロパティ](data-flow/recordset-destination-custom-properties.md)  
  
-   [SQL Server Compact Edition 変換先のカスタム プロパティ](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [SQL Server 変換先のカスタム プロパティ](data-flow/sql-server-destination-custom-properties.md)  
  
-   [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)  
  
-   [XML 入力元のカスタム プロパティ](data-flow/xml-source-custom-properties.md)  
  
##  <a name="components"></a>コンポーネントのプロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、データ フロー内のコンポーネントに <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントのプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|ComponentClassID|String|コンポーネントの CLSID。|  
|ContactInfo|String|コンポーネント開発者の連絡先情報。|  
|[説明]|String|データ フロー コンポーネントの説明。 このプロパティの既定値は、データ フロー コンポーネントの名前です。|  
|id|整数|コンポーネントのこのインスタンスを一意に識別する値。|  
|[IdentificationString]|String|コンポーネントを識別します。|  
|IsDefaultLocale|Boolean|コンポーネントが、それ自体が属するデータ フロー タスクのロケールを使用するかどうかを示します。|  
|LocaleID|整数|パッケージを実行する際、データ フロー コンポーネントが使用するロケール。 データ フロー コンポーネントでは、すべての Windows ロケールが使用できます。|  
|Name|String|データ フロー コンポーネントの名前。|  
|PipelineVersion|整数|コンポーネントを実行するように設計されたデータ フロー タスクのバージョン。|  
|UsesDispositions|Boolean|コンポーネントにエラー出力があるかどうかを示します。|  
|[ValidateExternalMetadata]|Boolean|外部列のメタデータを検証するかどうかを示します。 このプロパティの既定値は `True` です。|  
|Version|整数|コンポーネントのバージョン。|  
  
##  <a name="inputs"></a>入力プロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、変換および変換先には入力があります。 データ フロー内のコンポーネントの入力は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントの入力のプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|[説明]|String|入力の説明。|  
|ErrorOrTruncationOperation|String|行の処理中にエラーや切り捨てが発生する可能性がある場合、その種類を指定するオプションの文字列。|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|エラーの処理方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
|HasSideEffects|Boolean|コンポーネントが下流コンポーネントにアタッチされていない場合、およびがの`RunInOptimizedMode` `true`場合に、データフローの実行プランからコンポーネントを削除できるかどうかを示します。|  
|id|整数|入力を一意に識別する値。|  
|[IdentificationString]|String|入力を識別する文字列。|  
|IsSorted|Boolean|入力のデータを並べ替えるかどうかを示します。|  
|Name|String|入力の名前。|  
|SourceLocale|整数|入力データのロケール ID (LCID)。|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|行の処理中に発生した切り捨てを処理する方法を指定する値。 . 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
  
 変換先および一部の変換では、エラー出力がサポートされず、これらのコンポーネントの ErrorRowDisposition プロパティおよび TruncationRowDisposition プロパティは読み取り専用です。  
  
###  <a name="inputcolumns"></a>入力列のプロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、入力には入力列のコレクションが含まれています。 データ フロー内のコンポーネントの入力列は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントの入力列のプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|ComparisonFlags|整数|文字データ型を持つ列の比較を示すフラグの組。 詳しくは、「 [Comparing String Data](data-flow/comparing-string-data.md)」をご覧ください。|  
|[説明]|String|入力列を説明します。|  
|ErrorOrTruncationOperation|String|行の処理中にエラーや切り捨てが発生する可能性がある場合、その種類を指定するオプションの文字列。|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|エラーの処理方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|出力列に割り当てられた外部メタデータ列の ID。|  
|id|整数|入力列を一意に識別する値。|  
|[IdentificationString]|String|入力列を識別する文字列。|  
|LineageID|整数|上流列の ID。|  
|Name|String|入力列の名前。|  
|SortKeyPosition|整数|列を並べ替えるかどうか、並べ替える場合はその並べ替え順、および複数の列の並べ替えの順序を示す値。 値 **0** は、その列が並べ替えられないことを示します。  詳細については、「 [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」(マージ変換およびマージ結合変換用にデータを並べ替える方法) を参照してください。|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|行の処理中に発生した切り捨てを処理する方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
|UpstreamComponentName|String|上流コンポーネントの名前。|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|コンポーネントが入力列を使用する方法を指定する値。|  
  
 入力列には、後の「データ型プロパティ」で説明するデータ型プロパティもあります。  
  
##  <a name="outputs"></a>出力プロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、変換元および変換には出力があります。 データ フロー内のコンポーネントの出力は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントの出力のプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Boolean|出力がパスに接続されていない場合に、データ フロー エンジンが出力を削除するかどうかを指定する値。|  
|[説明]|String|出力を説明します。|  
|ErrorOrTruncationOperation|String|行の処理中にエラーや切り捨てが発生する可能性がある場合、その種類を指定するオプションの文字列。|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|エラーの処理方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
|ExclusionGroup|整数|相互排他的な出力のグループを識別する値。|  
|HasSideEffects|Boolean|コンポーネントが上流コンポーネントにアタッチされていない場合や、`RunInOptimizedMode` が `true` の場合に、データ フローの実行プランからコンポーネントを削除できるかどうかを示します。|  
|id|整数|出力を一意に識別する値。|  
|[IdentificationString]|String|出力を識別する文字列。|  
|IsErrorOut|Boolean|出力がエラー出力かどうかを示します。|  
|IsSorted|Boolean|出力を並べ替えるかどうかを示します。 既定値は `False` です。<br /><br /> ** \*重要\* \* **`IsSorted`プロパティの値をに設定し`True`ても、データは並べ替えられません。 このプロパティでは、データが既に並べ替えられている下流コンポーネントにヒントのみを提供します。 詳細については、「 [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」(マージ変換およびマージ結合変換用にデータを並べ替える方法) を参照してください。|  
|Name|String|出力の名前。|  
|SynchronousInputID|整数|出力に同期する入力の ID。|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|行の処理中に発生した切り捨てを処理する方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。|  
  
###  <a name="outputcolumns"></a>出力列のプロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、出力に出力列のコレクションが含まれています。 データ フロー内のコンポーネントの出力列は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントの出力列のプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|ComparisonFlags|整数|文字データ型を持つ列の比較を示すフラグの組。 詳しくは、「 [Comparing String Data](data-flow/comparing-string-data.md)」をご覧ください。|  
|[説明]|String|出力列を説明します。|  
|ErrorOrTruncationOperation|String|行の処理中にエラーや切り捨てが発生する可能性がある場合、その種類を指定するオプションの文字列。|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|エラーの処理方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。 既定値は `Fail component` です。|  
|ExternalMetadataColumnID|整数|出力列に割り当てられた外部メタデータ列の ID。|  
|id|整数|出力列を一意に識別する値。|  
|[IdentificationString]|String|出力列を識別する文字列。|  
|LineageID|整数|出力列の ID。 下流コンポーネントは、この値を使用して列を参照します。|  
|Name|String|出力列の名前。|  
|SortKeyPosition|整数|列を並べ替えるかどうか、並べ替える場合はその並べ替え順、および複数の列の並べ替えの順序を示す値。 値 **0** は、その列が並べ替えられないことを示します。 詳細については、「 [Sort Data for the Merge and Merge Join Transformations](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」(マージ変換およびマージ結合変換用にデータを並べ替える方法) を参照してください。|  
|SpecialFlags|整数|出力列の特殊なフラグを含む値。|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|行の処理中に発生した切り捨てを処理する方法を指定する値。 値は、`Fail component`、`Ignore failure`、および `Redirect row` です。 既定値は `Fail component` です。|  
  
 出力列には、データ型プロパティの組も含まれています。  
  
## <a name="external-metadata-column-properties"></a>外部メタデータ列のプロパティ  
 
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクト モデルでは、入力および出力に外部メタデータ列のコレクションを含めることができます。 データ フロー内のコンポーネントの外部メタデータ列は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> インターフェイスを実装します。  
  
 次の表は、データ フロー内のコンポーネントの外部メタデータ列のプロパティを示しています。 一部のプロパティの値は読み取り専用で、実行時にデータ フロー エンジンによって割り当てられます。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|[説明]|String|外部列を説明します。|  
|id|整数|列を一意に識別する値。|  
|[IdentificationString]|String|列を識別する文字列。|  
|Name|String|外部列の名前。|  
  
 外部メタデータ列には、データ型プロパティの組も含まれています。  
  
## <a name="data-type-properties"></a>データ型プロパティ  
 出力列および外部メタデータ列には、データ型プロパティの組が含まれています。 列のデータ型に応じて、プロパティは読み取り/書き込み可能または読み取り専用の場合があります。  
  
 次の表は、出力列および外部メタデータ列のデータ型プロパティを示しています。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|CodePage|整数|Unicode でない文字列データのコード ページを指定します。|  
|DataType|Integer (列挙)|列の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] データ型。 詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。|  
|Length|整数|列の長さ (文字数単位)。|  
|Precision|整数|数値列の有効桁数。|  
|スケール|整数|数値列の小数点以下桁数。|  
  
## <a name="see-also"></a>参照  
 [データフロー](data-flow/data-flow.md)   
 [変換のカスタムプロパティ](data-flow/transformations/transformation-custom-properties.md)   
 [パスのプロパティ](../../2014/integration-services/path-properties.md)   
 [式を使って設定できるデータ フロー プロパティ](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
