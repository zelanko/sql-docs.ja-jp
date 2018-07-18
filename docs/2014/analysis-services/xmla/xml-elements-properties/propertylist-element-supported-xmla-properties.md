---
title: サポートされる XMLA プロパティ (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- properties [XML for Analysis]
- XML for Analysis, properties
- XMLA, properties
ms.assetid: 5745f7b4-6b96-44d5-b77c-f2831a898e5e
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04e2b96df0cc549acadd50d80356a62bf327b7c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243962"
---
# <a name="supported-xmla-properties-xmla"></a>サポートされる XMLA プロパティ (XMLA)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 次の表に示したプロパティをサポートしています。 これらの一覧表示されているプロパティを使用する、[プロパティ](properties-element-xmla.md)の要素、 [Discover](../xml-elements-methods-discover.md)と[Execute](../xml-elements-methods-execute.md)メソッド。  
  
|名前|要素|  
|----------|-------------|  
|AxisFormat|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> 内で使用される形式を決定する[MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)結果セットの多次元データセットの軸を記述します。 このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*ClusterFormat*|`MDDataSet` 1 つまたは複数の軸から成る[CrossProduct](crossproduct-element-xmla.md)要素。|  
|*CustomFormat*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 使用して、 *TupleFormat*この設定の形式。|  
|*TupleFormat*|(既定値)`MDDataSet`軸は、1 つ以上含まれています。[タプル](tuple-element-xmla.md)要素。|  
  
 このプロパティは、`Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|BeginRange|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> `CellOrdinal` 属性値に対応する、0 から始まる整数値を含みます  (、`CellOrdinal`属性の一部である、[セル](cell-element-mddataset-xmla.md)内の要素、 [CellData](celldata-element-xmla.md)の`MDDataSet`)。<br /><br /> `EndRange` プロパティと共に使用され、クライアント アプリケーションはこのプロパティを使用して、コマンドによって返される OLAP データセットを特定の範囲のセルに制限することができます。 -1 が指定されている場合、`EndRange` プロパティで指定されたセルまでのすべてのセルが返されます。<br /><br /> このプロパティの既定値は-1 です。<br /><br /> このプロパティは、`Execute` メソッドで使用できます。|  
|Catalog|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> XMLA コマンドを送信するために [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとのセッションを確立する場合、このプロパティは OLE DB プロパティの DBPROP_INIT_CATALOG と等価です。<br /><br /> セッション中にこのプロパティを設定してセッションの現在のデータベースを変更する場合、このプロパティは OLE DB プロパティの DBPROP_CURRENTCATALOG と等価です。<br /><br /> このプロパティの既定値は空の文字列です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|CatalogLocation|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_CATALOGLOCATION と等価です。<br /><br /> このプロパティの既定値は 0 で、DBPROPVAL_CL_START と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ClientProcessID|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 現在のセッションのプロセス スレッドの識別子 (ID) を含みます。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|CommitTimeout|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> 現在実行中の XMLA コマンドのコミット フェーズがロールバックするまでに待機する時間を秒数で指定します。 コミット フェーズなどの XMLA コマンドに対応[ステートメント](../xml-elements-commands/statement-element-xmla.md)または[プロセス](../xml-elements-commands/process-element-xmla.md)します。<br /><br /> 値 0 は、インスタンスが無制限に待機することを意味します。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|コンテンツ|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> `Discover` および `Execute` メソッドから返されるデータの種類を決定します。 このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|コマンドの構造を検証できます。コマンドは実行されません。|  
|*[スキーマ]*|要求されたコマンドに関連する XML スキーマを返します。 XML スキーマには、列情報やその他の情報が示されています。|  
|*データ*|要求されたデータだけを返します。|  
|*SchemaData*|(既定) スキーマ情報とデータを返します。|  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|Cube|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> コマンドのコンテキストを設定するキューブの名前を含みます。 コマンド自体は、多次元式 (MDX) の FROM 句内でなど、キューブ名を含む場合[選択](/sql/mdx/mdx-data-manipulation-select)ステートメントでは、このプロパティの設定は無視されます。<br /><br /> このプロパティの既定値は空の文字列です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DataSourceInfo|*使用方法*<br /> 必須。読み取り/書き込み用で、`String` 型のプロパティです。<br /><br /> *[説明]*<br /> インスタンス名など、データ ソースへの接続に必要な情報を含みます。<br /><br /> `DataSourceInfo` プロパティの内容は、クライアント アプリケーションが構築してインスタンスに設定するものではありません。 代わりに、クライアント アプリケーションを使用して、プロバイダーによってサポートされるデータ ソースを検索する必要があります、`Discover`を取得するメソッド、 [DISCOVER_DATASOURCES](../../schema-rowsets/xml/discover-datasources-rowset.md)行セット。 その後、クライアント アプリケーションは DISCOVER_DATASOURCES 行セットから取得したものと同じ値を `DataSourceInfo` プロパティの値として返します。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropCatalogTerm|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_CATALOGTERM と等価です。<br /><br /> このプロパティの既定値は "Database" です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropCatalogUsage|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_CATALOGUSAGE と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropColumnDefinition|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_COLUMNDEFINITION と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropConcatNullBehavior|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_CONCATNULLBEHAVIOR と等価です。<br /><br /> このプロパティの既定値は 1 で、DBPROPVAL_CB_NULL と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropDataSourceReadOnly|*使用方法*<br /> 省略可能、読み取り専用`Boolean`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_DATASOURCEREADONLY と等価です。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropGroupBy|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_GROUPBY と等価です。<br /><br /> このプロパティの既定値は 2 で、DBPROPVAL_GB_EQUALS_SELECT と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropHeterogeneousTables|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_HETEROGENEOUSTABLES と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropIdentifierCase|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_IDENTIFIERCASE と等価です。<br /><br /> このプロパティの既定値は 8 で、DBPROPVAL_IC_MIXED と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropInitMode|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_INIT_MODE と等価です。<br /><br /> このプロパティでサポートされている値は、DB_MODE_READWRITE と DB_MODE_READ だけです。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMaxIndexSize|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MAXINDEXSIZE と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMaxOpenChapters|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MAXOPENCHAPTERS と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMaxRowSize|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MAXROWSIZE と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMaxRowSizeIncludeBlob|*使用方法*<br /> 省略可。読み取り専用で、`Boolean` 型のプロパティです。<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MAXROWSIZEINCLUDESBLOB と等価です。<br /><br /> このプロパティの既定値は TRUE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMaxTablesInSelect|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MAXTABLESINSELECT と等価です。<br /><br /> このプロパティの既定値は 1 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdAutoexists|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> autoexists の動作を決定します。 このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0*|既定値で、1 と同じです。|  
|*1*|クエリ軸と名前付きセットに deep autoexists を適用します。 WHERE 句とサブセレクトを含めます。|  
|*2*|クエリ軸に deep autoexists を適用し、autoexists から名前付きセットを除外します。 WHERE 句とサブセレクトを含めます。|  
|*3*|WHERE 句と共に使用する名前付きセットには autoexists を適用しません。 WHERE 句と共に使用するクエリ軸には shallow autoexists を適用します。 サブセレクトと共に使用するクエリ軸とサブセレクトと共に使用する名前付きセットには deep autoexists を適用します。|  
  
 0 または空がこのプロパティの既定値です。 このプロパティは、セッションが作成されたときにだけ設定できるセッション プロパティです。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdCacheMode|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdCachePolicy|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdCacheRatio|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdCacheRatio2|*使用方法*<br /> 省略可能、読み取り/書き込み`Double`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdCompareCaseNotSensitiveStringFlags|*使用方法*<br /> 省略可。読み取り/書き込み用で、`Integer` 型のプロパティです。<br /><br /> *[説明]*<br /> 大文字と小文字を区別する文字列の比較、および並べ替え順序の機能を決定します。 このプロパティは、日本語のカタカナやヒンディー語のように、大文字と小文字をサポートしない文字セットの比較方法を制御します。 このプロパティの値はプロセス スレッドの最初の接続で設定され、同じプロセス スレッド内で後続のすべての接続に影響します。<br /><br /> 使用するフラグを確認するには、次の表を参照してください。|  
  
|名前|値|説明|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0x00000001*|場合は無視されます。|  
|適用なし|*0x00000002*|バイナリ比較です。 特定のアルファベット順ではなく、文字セット内の対応する値に基づいて文字が比較されます。|  
|NORM_IGNORENONSPACE|*0x00000010*|分音文字は無視されます。|  
|NORM_IGNORESYMBOLS|*0x00000100*|記号は無視されます。|  
|NORM_IGNOREKANATYPE|*0x00001000*|ひらがなとカタカナは区別されません。 比較を行うときに、対応するひらがなとカタカナは同じ文字と見なされます。|  
|NORM_IGNOREWIDTH|*0x00010000*|同じ文字を表す 1 バイトと 2 バイトの文字は区別されません。|  
|SORT_STRINGSORT|*0x00100000*|句読点は記号として扱われます。|  
  
 OLE DB における文字列比較の詳細については、MSDN ライブラリの Platform SDK セクションで「CompareString」を検索してください。  
  
 このプロパティの既定値はありません。  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdCompareCaseSensitiveStringFlags|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 大文字と小文字を区別しない文字列の比較、および並べ替え順序の機能を決定します。 このプロパティは、日本語のカタカナやヒンディー語のように、大文字と小文字をサポートしない文字セットの比較方法を制御します。 このプロパティの値はプロセス スレッドの最初の接続で設定され、同じプロセス スレッド内で後続のすべての接続に影響します。<br /><br /> 使用するフラグを確認するには、次の表を参照してください。|  
  
|名前|値|説明|  
|----------|-----------|-----------------|  
|NORM_IGNORECASE|*0x00000001*|場合は無視されます。|  
|適用なし|*0x00000002*|バイナリ比較です。 特定のアルファベット順ではなく、文字セット内の対応する値に基づいて文字が比較されます。|  
|NORM_IGNORENONSPACE|*0x00000010*|分音文字は無視されます。|  
|NORM_IGNORESYMBOLS|*0x00000100*|記号は無視されます。|  
|NORM_IGNOREKANATYPE|*0x00001000*|ひらがなとカタカナは区別されません。 比較を行うときに、対応するひらがなとカタカナは同じ文字と見なされます。|  
|NORM_IGNOREWIDTH|*0x00010000*|同じ文字を表す 1 バイトと 2 バイトの文字は区別されません。|  
|SORT_STRINGSORT|*0x00100000*|句読点は記号として扱われます。|  
  
 OLE DB における文字列比較の詳細については、MSDN ライブラリの Platform SDK セクションで「CompareString」を検索してください。  
  
 このプロパティの既定値はありません。  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdDebugMode|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdDynamicDebugLimit|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdFlattened2|*使用方法*<br /> 省略可能、読み取り/書き込み`Boolean`プロパティ<br /><br /> *[説明]*<br /> 親子階層が軸 0 で要求されない限り、親子階層のすべてのメンバーを、フラット化された結果として 1 つのテーブル列に出力します。 出力列用のレベル テンプレートは使用されません。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdMDXCompatibility|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> プレースホルダー メンバーが不規則階層または不均衡階層内で扱われる方法を決定します。 このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の旧バージョンとの互換性のために用意されている値で、1 と等価です。|  
|*1*|多様ディメンション内の階層に、ディメンション名と階層名を含むキャプションが付けられます。 キャプションの形式は次のとおりです。<br /><br /> [Dimension].[Hierarchy]<br /><br /> プレースホルダー メンバーは公開されます。|  
|*2*|多様ディメンション内の階層に、ディメンション名と階層名を含むキャプションが付けられます。キャプションの形式は次のとおりです。<br /><br /> [Dimension].[Hierarchy]<br /><br /> プレースホルダー メンバーは公開されません。|  
|*3*|(既定) プレースホルダー メンバーは公開されません。|  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdMDXUniqueNameStyle|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> ディメンション内のメンバーの一意な名前を生成するためのアルゴリズムを決定します。 このプロパティに使用できる値は、次の表のとおりです。<br /><br /> このプロパティの既定値は、6 です。|  
  
|値|説明|  
|-----------|-----------------|  
|*0*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の旧バージョンとの互換性のために用意されている値で、2 と等価です。|  
|*1*|次のように、キーのパスを使用するアルゴリズムを使用します。<br /><br /> [dim].&[key1].&[key2]|  
|*2*|次のように、名前のパスを使用するアルゴリズムを使用します。<br /><br /> [dim].[name1].&[name2]|  
|*3*|時間経過と共に変化しない、保証された一意の名前を使用します。|  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdSQLCompatibility|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMsmdSubQueries|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> サブクエリの動作を決定するビットマスクです。 このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0*|既定値は、以前のバージョンの互換性のある[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。<br /><br /> 計算されるメンバーまたは計算されるセットが、サブセレクトまたはサブキューブで許可されません。|  
|*1*|計算されるメンバーまたは計算されるセットが、サブセレクトまたはサブキューブで許可されます。 計算されるメンバーの先祖は、サブセレクトまたはサブキューブ空間に含まれません。|  
|*2*|計算されるメンバーまたは計算されるセットが、サブセレクトまたはサブキューブで許可されます。 計算されるメンバーの先祖が、サブセレクトまたはサブキューブ空間に含まれます。|  
  
 0 または空がこのプロパティの既定値です。  
  
 このプロパティは、セッションが作成されたときにだけ設定できるセッション プロパティです。  
  
 参照してください[サブセレクトとサブキューブで計算されるメンバー](../../multidimensional-models/mdx/calculated-members-in-subselects-and-subcubes.md)計算されるメンバーまたはサブセレクトとサブキューブで計算されるセットの動作の詳細についてはします。  
  
|名前|要素|  
|----------|-------------|  
|DbpropMsmdUseFormulaCache|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropMultiTableUpdate|*使用方法*<br /> 省略可能、読み取り専用`Boolean`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_MULTITABLEUPDATE と等価です。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropNullCollation|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_NULLCOLLATION と等価です。<br /><br /> このプロパティの既定値は 4 で、DBPROPVAL_NC_LOW と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropOrderByColumnsInSelect|*使用方法*<br /> 省略可能、読み取り専用`Boolean`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_ORDERBYCOLUMNSINSELECT と等価です。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropOutputParameterAvailable|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_OUTPUTPARAMETERAVAILABILITY と等価です。<br /><br /> このプロパティの既定値は 1 で、DBPROPVAL_OA_NOTSUPPORTED と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropPersistentIdType|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_PERSISTENTIDTYPE と等価です。<br /><br /> このプロパティの既定値は 4 で、DBPROPVAL_PT_NAME と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropPrepareAbortBehavior|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_PREPAREABORTBEHAVIOR と等価です。<br /><br /> このプロパティの既定値は 1 で、DBPROPVAL_CB_DELETE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropPrepareCommitBehavior|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_PREPARECOMMITBEHAVIOR と等価です。<br /><br /> このプロパティの既定値は 1 で、DBPROPVAL_CB_DELETE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropProcedureTerm|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_PROCEDURETERM と等価です。<br /><br /> このプロパティの既定値は "Calculated member" です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropQuotedIdentifierCase|*使用方法*<br /> 省略可。読み取り専用で、`Integer` 型のプロパティです。<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_QUOTEDIDENTIFIERCASE と等価です。<br /><br /> このプロパティの既定値は 8 で、DBPROPVAL_IC_MIXED と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSchemaUsage|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SCHEMAUSAGE と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSqlSupport|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SQLSUPPORT と等価です。<br /><br /> このプロパティの既定値は 512 で、DBPROPVAL_SQL_SUBMINIMUM と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSubqueries|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SUBQUERIES と等価です。<br /><br /> **メモ** サブクエリはデータ マイニング拡張機能 (DMX) でサポートされますが、このプロパティで扱うのは SQL でのサブクエリのサポートです。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSupportedTxnDdl|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SUPPORTEDTXNDDL と等価です。<br /><br /> このプロパティの既定値は 0 で、DBPROPVAL_TC_NONE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSupportedTxnIsoLevels|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SUPPORTEDTXNISOLEVELS と等価です。<br /><br /> このプロパティの既定値は 4096 で、DBPROPVAL_TI_READCOMMITTED と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropSupportedTxnIsoRetain|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SUPPORTEDTXNISORETAIN と等価です。<br /><br /> このプロパティの既定値は 292 で、DBPROPVAL_TR_ABORT_NO、DBPROPVAL_TR_COMMIT_NO、および DBPROPVAL_TR_NONE の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|DbpropTableTerm|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_TABLETERM と等価です。<br /><br /> このプロパティの既定値は "Cube" です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|Dialect|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> 以下の状況で使用される言語仕様を設定します。<br /><br /> -プロバイダーが最初に使用する言語の時間をプロバイダーは、クエリを実行しようとしています。<br />-失敗したクエリの結果として返される実行エラーに使用される言語。<br /><br /> `Dialect` プロパティは、クエリのほとんどが 1 つの特定の言語仕様を使用していると考えられる場合に使用できます。<br /><br /> 複数の言語仕様では、DMX と SQL のように、クエリ構文が似ている場合があります。 構文が似ているため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はクエリ構文から言語独自の仕様を推測できないことがあります。 ある言語仕様でクエリが実行できなかった場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは別の言語仕様でクエリの再実行を試みます。<br /><br /> `Dialect` プロパティが設定されている場合、プロバイダーが別の言語仕様でクエリの再実行を試みる場合でも、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は優先される言語仕様のクエリ実行エラーを返します。 たとえば、`Dialect` プロパティが MDGUID_DM に設定されているとします。 プロバイダーは最初にデータ マイニング クエリとしてクエリを実行しようとしますが、このクエリは失敗します。 そのため、プロバイダーは SQL クエリとしてクエリを再実行します。 しかし、この SQL クエリも失敗します。 `Dialect` プロパティの値は MDGUID_DM であるため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は SQL エラーのメッセージではなくデータ マイニング エラーのメッセージを返します。<br /><br /> `Dialect` プロパティが設定されていない場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は最後に使用された言語仕様のクエリ実行エラーを返します。 たとえば、`Dialect` が設定されていない場合で、データ マイニング クエリが失敗したとします。 プロバイダーはクエリを SQL として再実行します。 この SQL クエリも失敗します。 `Dialect` プロパティが設定されていないため、プロバイダーはデータ マイニング エラーのメッセージではなく、SQL エラーのメッセージを返します。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> このプロパティで使用できる言語仕様は、次の表のとおりです。|  
  
|名前|値|説明|  
|----------|-----------|-----------------|  
|DBGUID_SQL|*C8B522D7-5CF3-11CE-ADE5-00AA0044773D*|SQL パーサーが優先されます。|  
|MDGUID_DM|*62C58FED-CCA5-44F1-83B6-7B45682B3904*|DMX パーサーが優先されます。|  
|MDGUID_MDX|*A07CCCD0-8148-11D0-87BB-00C04FC33942*|MDX パーサーが優先されます。|  
  
|名前|要素|  
|----------|-------------|  
|Disable Prefetch Facts|*使用方法*<br /> 省略可能、読み取り/書き込み`Boolean`プロパティ<br /><br /> *[説明]*<br /> True に設定した場合、セッションの長さにあたる期間中、エンジンは値のプレフェッチをしなくなります。<br /><br /> このプロパティの既定値は`False`します。|  
|EffectiveRoles|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|EffectiveUserName|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> ph x="1" /&gt; インスタンスに接続するときに使用する、ユーザー名をオーバーライドするために使用するアカウントの名前を指定します。 プロパティの値は正規化されませんが、MDX [UserName](/sql/mdx/username-mdx)関数は、このプロパティを使用する場合に、リテラル値を返します。 このプロパティは、サーバー管理者のみが使用できます。<br /><br /> このプロパティでサポートされる SID の種類は、User、Group、Alias、WellKnownGroup、Computer です。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|EndRange|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> `CellOrdinal` 属性値に対応する、0 から始まる整数値を指定します  (`CellOrdinal` 属性は、`Cell` の `CellData` セクションの、`MDDataSet` 要素の一部です)。<br /><br /> `BeginRange` プロパティと共に使用され、クライアント アプリケーションはこのプロパティを使用して、コマンドによって返される OLAP データセットを特定の範囲のセルに制限することができます。 -1 が指定されている場合、`BeginRange` プロパティで指定されたセルからのすべてのセルが返されます。<br /><br /> このプロパティの既定値は-1 です。<br /><br /> このプロパティは、`Execute` メソッドで使用できます。|  
|ExecutionMode|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値は*Execute*します。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ForceCommitTimeout|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> 現在実行中の XMLA コマンドのコミット フェーズが、以前に発行されたコマンドを強制的にロールバックするまでに待機する時間を、秒数で指定します。 コミット フェーズは、`Statement` や `Process` などの XMLA コマンドに対応します。<br /><br /> 値 0 は、インスタンスが無制限に待機することを意味します。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|[形式]|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> `Discover` および `Execute` メソッドから返される結果セットの種類を決定します。 このプロパティに使用できる値は、次の表のとおりです。|  
  
 このプロパティの既定値は*ネイティブ*します。  
  
 このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。  
  
|値|説明|  
|-----------|-----------------|  
|*表形式*|設定を使用して結果を返す、[行セット](../xml-data-types/rowset-data-type-xmla.md)データ型。|  
|*多次元*|使用して、行セットを返します、 [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)データ型。|  
|*ネイティブ*|形式は明示的に指定されません。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はコマンドに応じて適切な形式を返します。 実際の結果の種類は、結果の名前空間によって識別されます。|  
  
|名前|要素|  
|----------|-------------|  
|ImpactAnalysis|*使用方法*<br /> 省略可能な書き込み専用`Boolean`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|LocaleIdentifier|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> `Discover` または `Execute` メソッドで使用されるロケール識別子 (LCID) について、読み取りまたは設定を行います。 言語識別子の 16 進数の完全なリストについては、MSDN ライブラリで「Language Identifiers」を検索してください。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MaximumRows|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropAggregateCellUpdate|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_AGGREGATECELL_UPDATE と等価です。<br /><br /> このプロパティの既定値は 4 で、MDPROPVAL_AU_SUPPORTED と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropAxes|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_AXES と等価です。<br /><br /> このプロパティの既定値は 2147483647 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropDrillFunctions|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> サーバーでのドリル関数のサポート レベルを決定します。 次の値を使用して、有効なビットマスクを作成します。<br /><br /> MDPROPVAL_MDF_BASIC (0x01)<br /><br /> MDPROPVAL_MDF_ASYMMETRIC (0x02)<br /><br /> MDPROPVAL_MDF_CALC_MEMBERS (0x04)<br /><br /> 既定値は次のとおりです。<br /><br /> 3 (SQL Server 2008 の場合)<br /><br /> 7 (SQL Server 2008 R2 および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の場合)<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropFlatteningSupport|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_FLATTENING_SUPPORT と等価です。<br /><br /> このプロパティの既定値は 1 で、MDPROPVAL_FS_FULL_SUPPORT と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxCaseSupport|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_CASESUPPORT と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxDescFlags|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_DESCFLAGS と等価です。<br /><br /> このプロパティの既定値は 7 で、MDPROPVAL_MD_BEFORE、MDPROPVAL_MD_AFTER、および MDPROPVAL_MD_SELF と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxFormulas|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_FORMULAS と等価です。<br /><br /> このプロパティの既定値は 63 で、MDPROPVAL_MF_WITH_CALCMEMBERS、MDPROPVAL_MF_WITH_NAMEDSETS、MDPROPVAL_MF_CREATE_CALCMEMBERS、MDPROPVAL_MF_CREATE_NAMEDSETS、MDPROPVAL_MF_SCOPE_SESSION、および MDPROPVAL_MF_SCOPE_GLOBAL の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxJoinCubes|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_JOINCUBES と等価です。<br /><br /> このプロパティの既定値は 1 で、MDPROPVAL_MJC_SINGLECUBE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxMemberFunctions|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_MEMBER_FUNCTIONS と等価です。<br /><br /> このプロパティの既定値は 15 で、使用可能なすべての OLE DB 値の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxNamedSets|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> 次の表に示す値のビットマスクです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0x01*|MDPROPVAL_MNS_BASIC|  
|*0x02*|MDPROPVAL_MNS_DYNAMIC|  
|*0x04*|MDPROPVAL_MNS_DISPLAYFOLDER|  
|*0x08*|MDPROPVAL_MNS_CAPTION|  
  
 このプロパティの既定値は 15 です。  
  
|名前|要素|  
|----------|-------------|  
|MdpropMdxNonMeasureExpressions|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_NONMEASURE_EXPRESSIONS と等価です。<br /><br /> このプロパティの既定値は 0 で、MDPROPVAL_NME_ALLDIMENSIONS と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxNumericFunctions|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_NUMERIC_FUNCTIONS と等価です。<br /><br /> このプロパティの既定値は 2047 で、MDPROPVAL_MNF_MEDIAN、MDPROPVAL_MNF_VAR、MDPROPVAL_MNF_STDDEV、MDPROPVAL_MNF_RANK、MDPROPVAL_MNF_AGGREGATE、MDPROPVAL_MNF_COVARIANCE、MDPROPVAL_MNF_CORRELATION、MDPROPVAL_MNF_LINREGSLOPE、MDPROPVAL_MNF_LINREGVARIANCE、MDPROPVAL_MNF_LINREG2、および MDPROPVAL_MNF_LINREGPOINT の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxObjQualification|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_OBJQUALIFICATION と等価です。<br /><br /> このプロパティの既定値は 496 で、MDPROPVAL_MOQ_DIM_HIER、MDPROPVAL_MOQ_DIMHIER_LEVEL、MDPROPVAL_MOQ_DIMHIER_MEMBER、MDPROPVAL_MOQ_LEVEL_MEMBER、および MDPROPVAL_MOQ_MEMBER_MEMBER の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxOuterReference|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_OUTERREFERENCE と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxQueryByProperty|*使用方法*<br /> 省略可能、読み取り専用`Boolean`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_QUERYBYPROPERTY と等価です。<br /><br /> このプロパティの既定値は TRUE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxRangeRowset|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_RANGEROWSET と等価です。<br /><br /> このプロパティの既定値は 4 で、MDPROPVAL_RR_UPDATE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxSetFunctions|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_SET_FUNCTIONS と等価です。<br /><br /> このプロパティの既定値は 524287 で、MDPROPVAL_MSF_TOPPERCENT、MDPROPVAL_MSF_BOTTOMPERCENT、MDPROPVAL_MSF_TOPSUM、MDPROPVAL_MSF_BOTTOMSUM、MDPROPVAL_MSF_PERIODSTODATE、MDPROPVAL_MSF_LASTPERIODS、MDPROPVAL_MSF_YTD、MDPROPVAL_MSF_QTD、MDPROPVAL_MSF_MTD、MDPROPVAL_MSF_WTD、MDPROPVAL_MSF_DRILLDOWNMEMBER、MDPROPVAL_MSF_DRILLDOWNLEVEL、MDPROPVAL_MSF_DRILLDOWNMEMBERTOP、MDPROPVAL_MSF_DRILLDOWNMEMBERBOTTOM、MDPROPVAL_MSF_DRILLDOWNLEVEL、MDPROPVAL_MSF_DRILLDOWNLEVELTOP、MDPROPVAL_MSF_DRILLDOWNLEVELBOTTOM、MDPROPVAL_MSF_DRILLUPMEMBER、MDPROPVAL_MSF_DRILLUPLEVEL、および MDPROPVAL_MSF_TOGGLEDRILLSTATE の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxSlicer|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_SLICER と等価です。<br /><br /> このプロパティの既定値は 2 で、MDPROPVAL_MS_SINGLETUPLE と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxStringCompop|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_MDX_STRING_COMPOP と等価です。<br /><br /> このプロパティの既定値は 15 で、MDPROPVAL_MSC_LESSTHAN、MDPROPVAL_MSC_GREATERTHAN、MDPROPVAL_MSC_LESSTHANEQUAL、および MDPROPVAL_MSC_GREATERTHANEQUAL の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdpropMdxSubQueries|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> SQL Server 2014 では、このプロパティの既定値は 63 です。<br /><br /> SQL Server 2008 R2 および [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では、このプロパティの既定値は 31 です。<br /><br /> SQL Server 2008 では、このプロパティの既定値は 15 です。<br /><br /> MDX のサブクエリのサポートのレベルを示します。 次の表に示す値のビットマスクです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0x01*|MDPROPVAL_MSQ_BASIC|  
|*0x02*|MDPROPVAL_MSQ_ARBITRARYSHAPE|  
|*0x04*|MDPROPVAL_MSQ_NONVISUAL|  
|*0x08*|MDPROPVAL_MSQ_CALCMEMBERS|  
  
|||  
|-|-|  
|*0x10*|MDPROPVAL_MSQ_CALCMEMBERS2|  
  
|名前|要素|  
|----------|-------------|  
|MdpropNamedLevels|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_NAMED_LEVELS と等価です。<br /><br /> このプロパティの既定値は 3 で、MDPROPVAL_NL_NAMEDLEVELS と MDPROPVAL_NL_NUMBEREDLEVELS の組み合わせと等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|MdxMissingMemberMode|*使用方法*<br /> 省略可能な書き込み専用`String`プロパティ<br /><br /> *[説明]*<br /> 欠落したメンバーを MDX ステートメントで無視するかどうかを示します。<br /><br /> このプロパティは OLE DB プロパティの DBPROP_MDX_MISSING_MEMBER_MODE と等価です。<br /><br /> このプロパティの既定値は*既定*します。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*[Default]*|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによって生成される値を使用します。|  
|*Error*|エラーを生成します。|  
|*無視します。*|欠落したメンバーを常に無視します。|  
  
|名前|要素|  
|----------|-------------|  
|MDXSupport|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> MDX のサポートの程度を記述する列挙を指定します。<br /><br /> `Value` = *Core*すべての MDX オプションがサポートされます。<br /><br /> 列挙体を含む唯一の値は、現時点では、 *Core*します。 将来のリリースでは、他の値もこの列挙に定義されます。<br /><br /> このプロパティの既定値は*Core*します。<br /><br /> このプロパティは、`Discover` メソッドで使用できます。|  
|NonEmptyThreshold|*使用方法*<br /> 省略可。読み取り/書き込み用で、`Integer` 型のプロパティです。<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|パスワード|**このプロパティはサポートされなくなりました。**<br /><br /> *使用方法*<br /> 省略可。書き込み専用で、`String` 型のプロパティです。<br /><br /> *[説明]*<br /> 旧バージョンとの互換性のために用意されているプロパティで、`Execute` または `Discover` メソッドで使用された場合には無視され、エラーは生成されません。|  
|ProviderName|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_DBMSNAME と等価です。<br /><br /> このプロパティの既定値は "OLAP Server" です。<br /><br /> このプロパティは、`Discover` メソッドで使用できます。|  
|ProviderType|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_DATASOURCE_TYPE と等価です。<br /><br /> このプロパティの既定値は、6 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ProviderVersion|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_DBMSVER と等価です。<br /><br /> このプロパティの既定値は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのバージョンです。<br /><br /> このプロパティは、`Discover` メソッドで使用できます。|  
|ReadOnlySession|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|RealTimeOlap|*使用方法*<br /> 省略可能、読み取り/書き込み`Boolean`プロパティ<br /><br /> *[説明]*<br /> TRUE に設定されている場合は、テーブル通知をリッスンするすべてのパーティションに対するクエリが、キャッシュをバイパスしてリアルタイムで実行されます。 このプロパティは OLE DB プロパティの DBPROP_MSMD_REAL_TIME_OLAP と等価です。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ReturnCellProperties|*使用方法*<br /> 省略可能、読み取り/書き込み`Boolean`プロパティ<br /><br /> *[説明]*<br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ロール|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> クライアント アプリケーションが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに接続する場合に使用するロール名のコンマ区切りの文字列を指定します。 このプロパティを使用すると、ユーザーは現在使用しているロール以外のロールを使用して接続できます。 たとえば、サーバー管理者が、あるロールに許可された権限をテストするために、そのロールのメンバーとしてキューブに接続したい場合に使用できます。 このプロパティを使用して接続するには、このユーザーは指定されたロールのメンバーである必要があります。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> **メモ** ロール名の大文字と小文字は区別されます。 **使用しない**コンマ区切りのロール名の間のスペース。 スペースを使用すると、保護されたセルのセットに対するクエリによって、エラーおよび予期しない結果が返される可能性があります。|  
|SafetyOptions|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> クライアント アプリケーションが安全でないライブラリを登録して読み込めるかどうかを決定します。<br /><br /> このプロパティの値は、ローカル キューブで PASSTHROUGH キーワードを許可するかどうかも決定します。 以下の場合に、エラーが発生します。<br /><br /> 場合、クライアント アプリケーションが、PASSTHROUGH キーワードを含む INSERT INTO ステートメントを使用してローカル キューブを作成しようとするとします。<br />場合、クライアント アプリケーションが、PASSTHROUGH キーワードを使用する INSERT INTO ステートメントを含むローカル キューブを更新しようとするとします。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> このプロパティに使用できる値は、次の表のとおりです。|  
  
|名前|値|説明|  
|----------|-----------|-----------------|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_DEFAULT|*0*|この値は、DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE として扱われます。<br /><br /> ローカル キューブへの接続の場合、この値は CREATECUBE 接続文字列プロパティが使用されるかどうかによって異なります。 CREATECUBE 接続文字列プロパティが使用される場合、この値は DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL と同じです。 そうでない場合、この値は DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE と同じです。|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL|*1*|この値は、初期化とスクリプティングに関する安全性を検証せずに、すべてのユーザー定義関数ライブラリを有効にします。 ローカル キューブへの接続の場合、この値を指定すると、ストアド プロシージャの使用、および INSERT INTO ステートメントでの PASSTHROUGH キーワードの使用が有効になります。<br /><br /> **このオプションはお勧めしません**します。|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_SAFE|*2*|この値は、特定のユーザー定義関数ライブラリのすべてのクラスを検査して、初期化とスクリプティングに関する安全性を確認するように設定します。 ローカル キューブへの接続の場合、この値を指定すると、INSERT INTO ステートメント内での PASSTHROUGH キーワードの使用、および PermissionSet プロパティが Safe に設定されていないストアド プロシージャの使用ができなくなります。<br /><br /> この値でのアクションも削除されます、 [MDSCHEMA_ACTIONS](../../schema-rowsets/ole-db-olap/mdschema-actions-rowset.md) ACTION_TYPE 列で、いずれかのコマンドまたは HTML の値があるか、URL で ACTION_TYPE 列の値と値にはないコンテンツの列にあるスキーマ行セット"http://"または"https://"で開始します。|  
|DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_NONE|*3*|この値は、セッション中にユーザー定義関数が使用されないようにします。 ローカル キューブへの接続の場合、この値を使用すると、すべてのストアド プロシージャの使用、および INSERT INTO ステートメントでの PASSTHROUGH キーワードの使用ができなくなります。<br /><br /> さらに、この値を指定すると、MDSCHEMA_ACTIONS スキーマ行セット内のすべてのアクションが削除されます。|  
  
|名前|要素|  
|----------|-------------|  
|SecuredCellValue|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> 保護されたセルへのアクセスを試行した場合に返されるエラー コードと、`Value` および `Formatted Value` セル プロパティの値を指定します。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*0*|(既定値)以前のバージョンと互換性のため、この値は、同じ*1*します。 この既定値の意味は、将来のバージョンでは変更される可能性があります。|  
|*1*|戻り値 : HRESULT = NO_ERROR<br /><br /> セルの `Value` プロパティには、結果がバリアント データ型として格納されます。 `Formatted Value` には "#N/A" という文字列が返されます。|  
|*2*|HRESULT の値としてエラーを返します。|  
|*3*|`Value` および `Formatted Value` プロパティの両方に NULL を返します。|  
|*4*|`Value` プロパティに数値の 0 を返し、`Formatted Value` プロパティに書式設定された 0 を返します。 たとえば、`Formatted Value` プロパティが "#.##" であるセルの `Format` プロパティには、0.00 が返されます。|  
|*5*|`Value` および `Formatted Value` プロパティの両方に "#SEC" という文字列を返します。|  
  
|名前|要素|  
|----------|-------------|  
|ServerName|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの DBPROP_SERVERNAME と等価です。<br /><br /> このプロパティの既定値は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの名前です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|ShowHiddenCubes|*使用方法*<br /> 省略可能、読み取り/書き込み`Boolean`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値は FALSE です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|SQLQueryMode|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> 計算を SQL クエリに含めるかどうかを決定します。<br /><br /> このプロパティの既定値は*Calculated*します。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。<br /><br /> このプロパティに使用できる値は、次の表のとおりです。|  
  
|値|説明|  
|-----------|-----------------|  
|*データ*|計算は含まれません。|  
|*計算*|計算が返されます。|  
|*IncludeEmpty*|計算と空の行が返されます。|  
  
|名前|要素|  
|----------|-------------|  
|SQLSupport|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティの既定値は 512 文字です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|SspropInitAppName|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> クライアント アプリケーションの名前を含みます。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|SspropInitPacketsize|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> クライアント アプリケーションの ID を含みます。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|SspropInitWsid|*使用方法*<br /> 省略可能、読み取り/書き込み`String`プロパティ<br /><br /> *[説明]*<br /> クライアント ワークステーションの ID を含みます。<br /><br /> このプロパティの既定値はありません。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|StateSupport|*使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> 状態保持のサポートの程度を指定します。<br /><br /> *[なし]* = <br />                        状態保持はサポートされません。<br /><br /> *セッション*= 状態保持はセッションのサポートを通じて提供されます。<br /><br /> 状態保持とセッションのサポートの詳細については、次を参照してください。[接続の管理とセッション&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)します。<br /><br /> このプロパティの既定値は*セッション*します。<br /><br /> このプロパティは、`Discover` メソッドで使用できます。|  
|Timeout|*使用方法*<br /> 省略可能、読み取り/書き込み`Integer`プロパティ<br /><br /> *[説明]*<br /> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスが要求の正常な完了を待機する最大時間を秒数で指定します。この時間を超えると、エラーを返します。 このプロパティは、書き戻しテーブルへの更新が正常に完了するのをインスタンスが待機する最大時間も決定します。この時間を超えると、エラーを返します。これは、接続文字列プロパティの Writeback Timeout と等価です。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|TransactionDDL|*使用方法*<br /> 省略可能、読み取り専用`Integer`プロパティ<br /><br /> *[説明]*<br /> 将来使用するために予約されています。<br /><br /> このプロパティの既定値は 0 です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
|UserName|このプロパティはサポートされなくなりました。<br /><br /> *使用方法*<br /> 省略可能、読み取り専用`String`プロパティ<br /><br /> *[説明]*<br /> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによってコマンドに関連付けられるユーザー名を返す文字列を指定します。 旧バージョンとの互換性のために用意されているプロパティで、`Execute` または `Discover` メソッドで使用された場合には無視され、エラーは生成されません。 このプロパティは OLE DB プロパティの DBPROP_USERNAME と等価です。<br /><br /> このプロパティの既定値は、現在のセッションまたは接続を開いたユーザー名です。<br /><br /> このプロパティは、`Execute` メソッドで使用できます。|  
|VisualMode|*使用方法*<br /> 省略可能な書き込み専用`Integer`プロパティ<br /><br /> *[説明]*<br /> このプロパティは OLE DB プロパティの MDPROP_VISUALMODE と等価です。<br /><br /> このプロパティの既定値は 0 で、DBPROPVAL_VISUAL_MODE_DEFAULT と等価です。<br /><br /> このプロパティは、`Discover` メソッドおよび `Execute` メソッドで使用できます。|  
  
## <a name="see-also"></a>参照  
 [PropertyList 要素&#40;XMLA&#41;](propertylist-element-xmla.md)  
  
  
