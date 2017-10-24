---
title: "DMSCHEMA_MINING_COLUMNS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_COLUMNS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_COLUMNS rowset
ms.assetid: ae35ccde-4438-46f4-8611-40b2b1a42fce
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa9ee7c66193eb84f883ba0500a8617421f2228e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingcolumns-rowset"></a>DMSCHEMA_MINING_COLUMNS 行セット
  すべてのデータ マイニング モデルの個々 の列について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 この行セットは、現在のカタログに制限されます。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_COLUMNS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|カタログ名。 モデルがメンバーとして含まれているデータベースの名前を使用して設定されます。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|修飾されていないスキーマ名。 は、この列はサポートされていない[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|マイニング モデル名。 この列には、列が関連付けられているマイニング モデルの名前が格納され、空になることはありません。|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|列の名前です。|  
|**COLUMN_GUID**|**DBTYPE_GUID 型**|列の GUID。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**COLUMN_PROPID**|**DBTYPE_UI4**|列のプロパティ ID。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**|列の位置を表す序数。 列には 1 から始まる連番が付けられます。 この列に含まれる**NULL**列に安定した序数がない場合。|  
|**COLUMN_HAS_DEFAULT**|**DBTYPE_BOOL**|列に既定値があるかどうかを示すブール値。<br /><br /> **TRUE** 、列がそれ以外の場合、既定値を持つ場合**FALSE**です。|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**|列の既定値です。<br /><br /> 既定値は場合、 **NULL**値、 **COLUMN_HASDEFAULT**が含まれています**TRUE**、この列が含まれています**NULL**です。|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**|列の特性を記述するビットマスク。 **DBCOLUMNFLAGS**列挙型は、対応するビットマスクのビットを指定します。 この列が空になることはありません。|  
|**によって IS_NULLABLE**|**DBTYPE_BOOL**|列で NULL 値が許容されるかどうかを示すブール値。<br /><br /> **FALSE**に null 値、それ以外の列がわかっている場合**TRUE**です。|  
|**DATA_TYPE**|**DBTYPE_UI2**|列のデータ型のインジケーターです。 次の一覧に、返されるインジケーターの種類の例を示します。<br /><br /> "**テーブル**"を返します**DBTYPE_HCHAPTER**です。<br /><br /> "**テキスト**"を返します**DBTYPE_WCHAR**です。<br /><br /> "**長い**"を返します**DBTYPE_I8**です。<br /><br /> "**二重**"を返します**DBTYPE_R8**です。<br /><br /> "**日付**"を返します**DBTYPE_DATE**です。|  
|**TYPE_GUID**|**DBTYPE_GUID 型**|列のデータ型の GUID。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**VT_**です。|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**|列に格納できる値の最大の長さ。 文字、バイナリ、またはビットの列の場合、これは次のいずれかになります。<br /><br /> 長さが定義されている場合は、列の最大の長さを列の種類に応じて文字数、バイト数、またはビット数で表したものになります。 たとえば、 **char (5)** SQL テーブル内の列が 5 の最大長。<br /><br /> 列の長さが定義されていない場合は、データ型の最大の長さを列の種類に応じて文字数、バイト数、またはビット数で表したものになります。<br /><br /> 列にもデータ型にも最大の長さが定義されていない場合はゼロ (0) になります。<br /><br /> **NULL**他のすべての型の列|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**|列の型が文字またはバイナリである場合は、列の最大の長さ (単位はオクテット (バイト))。 ゼロ (0) の値は、列に最大の長さがないことを意味します。 この列に含まれる**NULL**他のすべての型の列です。|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**|列のデータ型は、数値データ型以外の場合は、列の最大有効桁数**VARNUMERIC**です。<br /><br /> **NULL**かどうか、列のデータ型が数値でない、 **VARNUMERIC**です。<br /><br /> データ型を持つ列の有効桁数**DBTYPE_DECIMAL**または**DBTYPE_NUMERIC**列定義に依存します。|  
|**NUMERIC_SCALE**|**DBTYPE_I2**|列の型インジケーターがある場合、小数点の右側にある数字の数**DBTYPE_DECIMAL**、 **DBTYPE_NUMERIC**、または**DBTYPE_VARNUMERIC**です。 それ以外の場合、この列に含まれる**VT_**です。|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**|列のデータ型は DateTime または interval 型である場合は、列の日付/時刻有効桁数 (秒部分の数字の数)それ以外の場合、 **NULL**です。|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**|文字セットが定義されているカタログ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**|文字セットが定義されている非修飾スキーマ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**|文字セット名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**|照合順序が定義されているカタログ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**|照合順序が定義されている非修飾スキーマ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**COLLATION_NAME**|**DBTYPE_WSTR**|照合順序名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**|ドメインが定義されているカタログ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**|ドメインが定義されている非修飾スキーマ名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**ドメイン名**|**DBTYPE_WSTR**|ドメイン名。 は、この列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**DESCRIPTION**|**DBTYPE_WSTR**|列のわかりやすい説明ではこの列はサポートされていない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 常に含まれている**NULL**です。|  
|**DISTRIBUTION_FLAG**|**DBTYPE_WSTR**|列の統計分布の記述。 この列の値は次のいずれかになります。<br /><br /> "**標準**"<br /><br /> "**LOG_NORMAL**"<br /><br /> "**UNIFORM**"|  
|**CONTENT_TYPE**|**DBTYPE_WSTR**|列のコンテンツの記述。 この列の値は次のいずれかになります。<br /><br /> "**キー**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUOUS**"<br /><br /> "**DISCRETIZED (**[引数]**)**"<br /><br /> "**ORDERED**"<br /><br /> "**KEY TIME**"<br /><br /> "**CYCLICAL**"<br /><br /> "**確率**"<br /><br /> "**差異**"<br /><br /> "**STDEV**"<br /><br /> "**サポート**"<br /><br /> "**PROBABILITY_VARIANCE**"<br /><br /> "**PROBABILITY_STDEV**"<br /><br /> **"キー シーケンス**"|  
|**MODELING_FLAG**|**DBTYPE_WSTR**|フラグのコンマ区切りの一覧。 定義済みフラグには次のものがあります。<br /><br /> "**MODEL_EXISTENCE_ONLY**"<br /><br /> "**リグレッサー**"<br /><br /> アルゴリズムに固有のモデリング フラグがこの列に格納されることもあります。|  
|**IS_RELATED_TO_KEY**|**DBTYPE_BOOL**|列がキーに関連するかどうかを示すブール値。<br /><br /> **TRUE**この列がキーに関連付けられている場合。 キーが 1 つの列である場合、 **RELATED_ATTRIBUTE**フィールドは、その列名を含めることができます必要に応じて。|  
|**RELATED_ATTRIBUTE**|**DBTYPE_WSTR**|対象の列を現在の列が関連するかが特殊なプロパティの名前。|  
|**IS_INPUT**|**DBTYPE_BOOL**|列が入力列であるかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**場合は、入力列です。|  
|**IS_PREDICTABLE**|**DBTYPE_BOOL**|列が予測可能列であるかどうかを示すブール値。<br /><br /> **TRUE**列が予測可能な場合です。|  
|**CONTAINING_COLUMN**|**DBTYPE_WSTR**|名前、**テーブル**この列を含む列。 この列に含まれる**NULL**列が別の列に含まれていない場合。|  
|**PREDICTION_SCALAR_FUNCTIONS**|**DBTYPE_WSTR**|列で実行できるスカラー関数のコンマ区切りの一覧。|  
|**PREDICTION_TABLE_FUNCTIONS**|**DBTYPE_WSTR**|列に適用できる関数のコンマ区切りの一覧。 これらの関数はテーブルを返します。 一覧の形式は次のとおりです。<br /><br /> `<function name>(<column1> [, <column2>], ...)`<br /><br /> この形式により、クライアント アプリケーションでそれぞれの関数のシグネチャ (パラメーターの一覧) を判断することができます。|  
|**IS_POPULATED**|**DBTYPE_BOOL**|この列が一連の可能な値でトレーニングされているかどうかを示すブール値。<br /><br /> **TRUE**列が使用可能な値のセットでトレーニングされている場合。<br /><br /> 含む**FALSE**列が設定されていない場合。|  
|**PREDICTION_SCORE**|**DBTYPE_R8**|列の予測におけるモデルのスコア。 スコアはモデルの精度を測定するために使用されます。|  
|**SOURCE_COLUMN**|**DBTYPE_WSTR**|現在のマイニング列のソース マイニング構造列の名前。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_COLUMNS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**MODEL_NAME**|**DBTYPE_WSTR**|省略可。|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

