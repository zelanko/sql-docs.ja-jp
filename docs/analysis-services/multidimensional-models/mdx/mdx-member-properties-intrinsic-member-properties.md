---
title: "固有メンバー プロパティ (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1b3dfd57447e95c22a468e3635030f8973fcc2bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-member-properties---intrinsic-member-properties"></a>MDX メンバーのプロパティ - 固有メンバー プロパティ
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、カスタム アプリケーションで使用する追加のデータまたはメタデータを返したり、モデルの調査や構築を支援したりするために、クエリに含めることができるディメンション メンバーの固有プロパティを公開します。 SQL Server クライアント ツールを使用している場合は、SQL Server Management Studio (SSMS) で固有プロパティを表示できます。  
  
 固有プロパティには **ID**、 **KEY**、 **KEYx**、 **NAME**など があります。これらは、各メンバーによって任意のレベルで公開されるプロパティです。 特に、 **LEVEL_NUMBER** や **PARENT_UNIQUE_NAME**などのように位置情報を返すこともできます。  
  
 クエリの作成方法や、クエリの実行に使用しているクライアント アプリケーションに応じて、メンバー プロパティが結果セットに表示される場合と表示されない場合があります。 クエリのテストまたは実行に SQL Server Management Studio を使用している場合は、結果セットのメンバーをダブルクリックして [メンバーのプロパティ] ダイアログ ボックスを開くと、各固有メンバー プロパティの値が表示されます。  
  
 ディメンション メンバー プロパティの使用および表示の概要については、「 [SSMS で MDX クエリ ウィンドウ内の SSAS メンバー プロパティを表示する](http://go.microsoft.com/fwlink/?LinkId=317362)」を参照してください。  
  
> [!NOTE]  
>  1999 年 3 月 (2.6) OLE DB 仕様の OLAP セクションに準拠するプロバイダーとして、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はこのトピックに記述されている固有メンバー プロパティをサポートします。  
>   
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 以外のプロバイダーは、この他にも追加の固有メンバー プロパティをサポートする場合があります。 他のプロバイダーによってサポートされる固有メンバー プロパティについての詳細は、各プロバイダーに付属の資料を参照してください。  
  
## <a name="types-of-member-properties"></a>メンバー プロパティの種類  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] がサポートする固有メンバー プロパティには、次の 2 種類があります。  
  
 状況依存メンバー プロパティ  
 この種類のメンバー プロパティは、特定の階層またはレベルのコンテキストで使用する必要があり、特定のディメンションまたはレベルの各メンバーに関する値を提供します。  
  
 次の例で、 **KEY** プロパティのパスがどのように含まれているかを確認してください。 `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`  
  
 非状況依存メンバー プロパティ  
 この種類のメンバー プロパティは、特定のディメンションまたはレベルのコンテキストで使用できず、軸上のすべてのメンバーに関する値を返します。  
  
 非状況依存のプロパティはスタンドアロンであり、パス情報を含みません。 次の例で、 **PARENT_UNIQUE_NAME** にディメンションまたはレベルが指定されていないことを確認してください。 `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`  
  
 固有メンバー プロパティが状況依存/非状況依存のどちらの場合にも、次のような使用上の規則があります。  
  
-   軸上に射影されているディメンション メンバーに関連する固有メンバー プロパティだけを指定できます。  
  
-   状況依存メンバー プロパティに対する要求を非状況依存固有メンバー プロパティと同じクエリの中に混合できます。  
  
-   プロパティを照会するには、キーワード **PROPERTIES** を使用します。  
  
 次のセクションでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で使用可能なさまざまな状況依存/非状況依存固有メンバー プロパティについて説明し、それぞれの種類のプロパティに対して **PROPERTIES** キーワードを使用する方法を示します。  
  
## <a name="context-sensitive-member-properties"></a>状況依存メンバー プロパティ  
 すべてのディメンション メンバーとレベル メンバーでは、状況に依存する固有メンバー プロパティがいくつかサポートされます。 次の表は、それらの状況依存プロパティを示しています。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**ID**|内部的に管理されるメンバー ID。|  
|**Key**|元のデータ型でのメンバー キーの値。 MEMBER_KEY は、旧バージョンとの互換性のために用意されています。  MEMBER_KEY プロパティの値は、非複合キーについては KEY0 と等しく、複合キーについては NULL です。|  
|**KEYx**|メンバーのキー (x はキーの序数で、0 から始まります)。 KEY0 は複合キーおよび非複合キーで使用できますが、主に複合キーで使用されます。<br /><br /> 複合キーの場合、KEY0、KEY1、KEY2 などは、全体として複合キーを形成します。 クエリでそれぞれを個別に使用すると、複合キーのその部分を返すことができます。 たとえば、KEY0 を指定すると複合キーの最初の部分が返され、KEY1 を指定すると複合キーの次の部分が返されます。<br /><br /> キーが非複合キーの場合、KEY0 は **Key**と同じです。<br /><br /> **KEYx** は、コンテキストの有無にかかわらず使用できることに注意してください。 このため、両方の一覧に表示されます。<br /><br /> このメンバー プロパティの使用方法の例については、「 [A Simple MDX Tidbit: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364)」(単純な MDX の情報: Key0、Key1、Key2) を参照してください。|  
|**Name**|メンバーの名前。|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a>状況依存プロパティの PROPERTIES の構文  
 この種類のメンバー プロパティは、特定のディメンションまたはレベルのコンテキストで使用し、特定のディメンションまたはレベルの各メンバーに関する値を提供します。  
  
 ディメンション メンバー プロパティの場合、プロパティ名の前に、そのプロパティが適用されるディメンションの名前を指定します。 次の例は、適切な構文を示しています。  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 レベル メンバー プロパティの場合、プロパティ名の前にレベル名だけを指定するか、プロパティ名の前にディメンション名とレベル名を両方とも指定することができます。 次の例は、適切な構文を示しています。  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 たとえば、 `[Sales]` ディメンション内で参照される各メンバーのすべての名前を取得する必要があるとします。 それらの名前を返すには、多次元 (MDX) クエリで次のステートメントを使用します。  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a>非状況依存メンバー プロパティ  
 すべてのメンバーでは、コンテキストに関係なく同じである固有メンバー プロパティがいくつかサポートされます。 これらのプロパティが提供する追加情報をアプリケーションで使用すれば、ユーザー エクスペリエンスを向上させることができます。  
  
 次の表は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]でサポートされる非状況依存の固有プロパティを示しています。  
  
> [!NOTE]  
>  MEMBERS スキーマ行セット内の列は、以下の表に示されている固有メンバー プロパティをサポートします。 **MEMBERS** スキーマ行セットの詳細については、「 [MDSCHEMA_MEMBERS 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)」を参照してください。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**CATALOG_NAME**|このメンバーが所属するキューブの名前。|  
|**CHILDREN_CARDINALITY**|メンバーが持つ子の数。 これは推定値の場合があります。したがって、この数値を正確な数として使用しないでください。 プロバイダーは、正確な数に最も近い推定値を返します。|  
|**CUSTOM_ROLLUP**|カスタム メンバー式。|  
|**CUSTOM_ROLLUP_PROPERTIES**|カスタム メンバー プロパティ。|  
|**DESCRIPTION**|メンバーに関する、人間が読める形式の説明。|  
|**DIMENSION_UNIQUE_NAME**|このメンバーが所属するディメンションの一意な名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**HIERARCHY_UNIQUE_NAME**|階層の一意な名前。 メンバーが複数の階層に所属している場合は、そのメンバーが所属する階層ごとに対応する行があります。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**IS_DATAMEMBER**|メンバーがデータ メンバーであるかどうかを示すブール値。|  
|**IS_PLACEHOLDERMEMBER**|メンバーがプレースホルダーであるかどうかを示すブール値。|  
|**KEYx**|メンバーのキー (x はキーの序数で、0 から始まります)。 KEY0 は複合キーおよび非複合キーに使用できます。<br /><br /> キーが非複合キーの場合、KEY0 は **Key**と同じです。<br /><br /> 複合キーの場合、KEY0、KEY1、KEY2 などは、全体として複合キーを形成します。 クエリでそれぞれを個別に参照すると、複合キーのその部分を返すことができます。 たとえば、KEY0 を指定すると複合キーの最初の部分が返され、KEY1 を指定すると複合キーの次の部分が返されます。<br /><br /> **KEYx** は、コンテキストの有無にかかわらず使用できることに注意してください。 このため、両方の一覧に表示されます。<br /><br /> このメンバー プロパティの使用方法の例については、「 [A Simple MDX Tidbit: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364)」(単純な MDX の情報: Key0、Key1、Key2) を参照してください。|  
|**LCID** *x*|ロケール ID の 16 進値で表現されたメンバー キャプションを変換したもの。 *x* はロケール ID の 10 進値です (たとえば、カナダ英語の場合は LCID1009)。 これは、データ ソースにバインドされたキャプション列が変換にある場合のみ使用できます。|  
|**LEVEL_NUMBER**|階層のルートからメンバーまでの距離。 ルートのレベルは 0 です。|  
|**LEVEL_UNIQUE_NAME**|メンバーが所属するレベルの一意な名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**MEMBER_CAPTION**|メンバーに関連付けられたラベルまたはキャプション。 キャプションの主な用途は、表示用です。 キャプションが存在しない場合、クエリの結果として **MEMBER_NAME**が返されます。|  
|**MEMBER_KEY**|元のデータ型でのメンバー キーの値。 MEMBER_KEY は、旧バージョンとの互換性のために用意されています。  MEMBER_KEY プロパティの値は、非複合キーについては KEY0 と等しく、複合キーについては NULL です。|  
|**MEMBER_NAME**|メンバーの名前。|  
|**MEMBER_TYPE**|メンバーの種類。 このプロパティの値は、次のいずれか 1 つです。<br /><br /> **MDMEMBER_TYPE_REGULAR**<br /><br /> **MDMEMBER_TYPE_ALL**<br /><br /> **MDMEMBER_TYPE_FORMULA**<br /><br /> **MDMEMBER_TYPE_MEASURE**<br /><br /> **MDMEMBER_TYPE_UNKNOWN**<br /><br /> <br /><br /> 注: MDMEMBER_TYPE_FORMULA は MDMEMBER_TYPE_MEASURE より優先順位が上です。 したがって、数式メンバー (計算されるメンバー) がメジャー ディメンションに存在する場合、計算されるメンバーの **MEMBER_TYPE** プロパティは MDMEMBER_TYPE_FORMULA です。|  
|**MEMBER_UNIQUE_NAME**|メンバーの一意な名前。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**MEMBER_VALUE**|元の型でのメンバーの値。|  
|**PARENT_COUNT**|このメンバーが持つ親の数。|  
|**PARENT_LEVEL**|階層のルート レベルからメンバーの親までの距離。 ルートのレベルは 0 です。|  
|**PARENT_UNIQUE_NAME**|メンバーの親の一意の名前。 ルート レベルのメンバーに対しては**NULL** を返します。 修飾によって一意な名前を生成するプロバイダーの場合、この名前の各コンポーネントは区切り記号付きです。|  
|**SKIPPED_LEVELS**|メンバーに関するスキップされたレベルの数。|  
|**UNARY_OPERATOR**|メンバーの単項演算子。|  
|**UNIQUE_NAME**|[dimension].[level].[key6] 形式で表す、メンバーの完全修飾名。|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a>非状況依存プロパティの PROPERTIES の構文  
 **PROPERTIES** キーワードを使用して固有の非状況依存メンバー プロパティを指定するには、次の構文を使用します。  
  
 `DIMENSION PROPERTIES Property`  
  
 この構文では、プロパティをディメンションまたはレベルで修飾できないことに注意してください。 プロパティを修飾できない理由は、非状況依存の固有メンバー プロパティが軸上のすべてのメンバーに適用されるためです。  
  
 たとえば、 **DESCRIPTION** 固有メンバー プロパティを指定する MDX ステートメントは次のような構文になります。  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 このステートメントは、軸ディメンション内の各メンバーに関する説明を返します。 たとえば *Dimension*`.DESCRIPTION` または *Level*`.DESCRIPTION`のように、ディメンションまたはレベルによってプロパティを修飾した場合、ステートメントは無効になります。  
  
### <a name="example"></a>例  
 固有プロパティを返す MDX クエリの例を次に示します。  
  
 **例 1: クエリで状況依存の固有プロパティを使用する**  
  
 次の例では、各製品カテゴリの親 ID、キー、および名前が返されます。 プロパティがメジャーとしてどのように公開されているかを確認してください。 これにより、SSMS の [メンバーのプロパティ] ダイアログではなく、クエリの実行時にセル セットのプロパティを表示できます。 既に配置されているキューブからメンバー メタデータを取得する場合に、このようなクエリを実行することがあります。  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 **例 2: 非状況依存の固有プロパティを使用する**  
  
 次の例は、非状況依存の固有プロパティの完全な一覧です。 SSMS でクエリを実行した後、個々のメンバーをクリックすると、[メンバーのプロパティ] ダイアログ ボックスにプロパティが表示されます。  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 **例 3: 結果セット内のデータとしてメンバー プロパティを返す**  
  
 次の例では、Adventure Works キューブの Product ディメンションに含まれる製品カテゴリ メンバーのキャプションを、指定されたロケールの言語で翻訳して返します。  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [PeriodsToDate &#40;MDX&#41;](../../../mdx/periodstodate-mdx.md)   
 [子と #40 です。MDX と #41 です。](../../../mdx/children-mdx.md)   
 [Hierarchize (& a) #40 です。MDX と #41 です。](../../../mdx/hierarchize-mdx.md)   
 [Count (セット) (MDX)](../../../mdx/count-set-mdx.md)   
 [フィルターと #40 です。MDX と #41 です。](../../../mdx/filter-mdx.md)   
 [AddCalculatedMembers & #40 です。MDX と #41 です。](../../../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel & #40 です。MDX と #41 です。](../../../mdx/drilldownlevel-mdx.md)   
 [プロパティ & #40 です。MDX と #41 です。](../../../mdx/properties-mdx.md)   
 [PrevMember & #40 です。MDX と #41 です。](../../../mdx/prevmember-mdx.md)   
 [メンバー プロパティの使用 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-function-reference-mdx.md)  
  
  
