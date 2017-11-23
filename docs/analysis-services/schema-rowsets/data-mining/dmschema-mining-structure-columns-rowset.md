---
title: "DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_STRUCTURE_COLUMNS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_STRUCTURE_COLUMNS rowset
ms.assetid: 81f25502-ac90-42f1-8ddf-7b0f9752ebfd
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 21b2e91cb0c388e3d61d5125366289d73c811f47
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingstructurecolumns-rowset"></a>DMSCHEMA_MINING_STRUCTURE_COLUMNS 行セット
  実行しているサーバーに展開されているすべてのマイニング構造の個々 の列について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DMSCHEMA_MINING_STRUCTURE_COLUMNS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||カタログ名。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||修飾されていないスキーマ名。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]スキーマをサポートしないため、この列は常に**NULL**です。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**||構造名。 この列を含めることはできません、 **NULL**です。|  
|**COLUMN_NAME**|**DBTYPE_WSTR**||列の名前です。 同じパターンを共有する列間でのみ、一意性が保証されます。 たとえば、入れ子になった 2 つの列が、同じ構造内の入れ子になった 2 つの異なるテーブルに属する場合、それらの列は同じ名前を持つことがあります。|  
|**COLUMN_GUID**|**DBTYPE_GUID 型**||列の GUID。 列を識別する Guid を使用しないプロバイダーを返す必要があります**NULL**この列にします。|  
|**COLUMN_PROPID**|**DBTYPE_UI4**||列のプロパティ ID。 列を含むプロパティ Id に関連付けないプロバイダーを返す必要があります**NULL**この列にします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]返します**NULL**この列にします。|  
|**ORDINAL_POSITION**|**DBTYPE_UI4**||列の序数。 列には 1 から始まる連番が付けられます。 **NULL**列に安定した序数がない場合。|  
|**COLUMN_HASDEFAULT**|**DBTYPE_BOOL**||この列に既定値があるかどうかを示すブール値。<br /><br /> **TRUE**列に既定値がある場合。<br /><br /> **FALSE**列には、既定値がない場合、またはそれが不明の場合、列が既定値を持つかどうか。|  
|**COLUMN_DEFAULT**|**DBTYPE_WSTR**||列の既定値です。 プロバイダーが公開される**DBCOLUMN_DEFAULTVALUE**ではなく**DBCOLUMN_HASDEFAULT** (ISO テーブル用) によって返される行セットで**icolumnsrowset::getcolumnsrowset**です。<br /><br /> 既定値は場合**NULL**、 **COLUMN_HASDEFAULT**は**TRUE**と**COLUMN_DEFAULT**列が、 **NULL**値。|  
|**COLUMN_FLAGS**|**DBTYPE_UI4**||列の特性を記述するビットマスク。 **DBCOLUMNFLAGS**列挙型は、対応するビットマスクのビットを指定します。 この列を含めることはできません、 **NULL**値。 有効な値は次のとおりです。<br /><br /> **DBCOLUMNFLAGS_ISNULLABLE** (**0x20**)<br /><br /> **DBCOLUMNFLAGS_MAYBENULL** (**0x40**)<br /><br /> **DBCOLUMNFLAGS_ISLONG** (**0x80**)|  
|**によって IS_NULLABLE**|**DBTYPE_BOOL**||この列に既定値があるかどうかを示すブール値。<br /><br /> **TRUE**列を含めることができる場合**NULL**です。**FALSE**、それ以外の場合。|  
|**DATA_TYPE**|**DBTYPE_UI2**||列のデータ型のインジケーターです。 例:<br /><br /> "**テーブル**"= **DBTYPE_HCHAPTER**<br /><br /> "**テキスト**"= **DBTYPE_WCHAR**<br /><br /> "**長い**"= **DBTYPE_I8**<br /><br /> "**二重**"= **DBTYPE_R8**<br /><br /> "**日付**"= **DBTYPE_DATE**|  
|**TYPE_GUID**|**DBTYPE_GUID 型**||列のデータ型の GUID。 データ型を識別する Guid を使用しないプロバイダーを返す必要があります**NULL**この列にします。|  
|**CHARACTER_MAXIMUM_LENGTH**|**DBTYPE_UI4**||列に格納できる値の最大の長さ。 文字、バイナリ、またはビットの列の場合、これは次のいずれかになります。<br /><br /> 長さが定義されている場合は、列の最大の長さ (単位は文字、バイト、またはビット)。 たとえば、SQL テーブルの `CHAR(5)` 列は、最大の長さが 5 になります。<br /><br /> 列の長さが定義されていない場合は、データ型の最大の長さ (単位は文字、バイト、またはビット)。<br /><br /> 列にもデータ型にも最大の長さが定義されていない場合はゼロ (0) になります。<br /><br /> **NULL**他のすべての型の列です。|  
|**CHARACTER_OCTET_LENGTH**|**DBTYPE_UI4**||列の型が文字またはバイナリである場合は、列の最大の長さ (単位はオクテット (バイト))。 ゼロ (0) の値は、列に最大の長さがないことを意味します。 **NULL**他のすべての型の列です。|  
|**NUMERIC_PRECISION**|**DBTYPE_UI2**||列のデータ型は、数値データ型以外の場合は、列の最大有効桁数**VARNUMERIC**です。**NULL**かどうか、列のデータ型が数値でない、 **VARNUMERIC**です。<br /><br /> データ型を持つ列の有効桁数**DBTYPE_DECIMAL**または**DBTYPE_NUM**ERIC が列の定義に依存します。|  
|**NUMERIC_SCALE**|**DBTYPE_I2**||列の型インジケーターがある場合、小数点の右側にある数字の数**DBTYPE_DECIMAL**、 **DBTYPE_NUMERIC**、または**DBTYPE_VARNUMERIC**です。 これは、それ以外の場合、 **NULL**です。|  
|**DATETIME_PRECISION**|**DBTYPE_UI4**||列が datetime 型または interval 型である場合は、列の DateTime の有効桁数 (秒部分の桁数)。 これは、列のデータ型が datetime でない場合は、 **NULL**です。|  
|**CHARACTER_SET_CATALOG**|**DBTYPE_WSTR**||文字セットが定義されているカタログ名。 **NULL**プロバイダーがカタログまたは各種文字セットをサポートしていない場合。|  
|**CHARACTER_SET_SCHEMA**|**DBTYPE_WSTR**||文字セットが定義されている、修飾されていないスキーマ名。 **NULL**プロバイダーはスキーマまたは各種文字セットをサポートしていない場合。|  
|**CHARACTER_SET_NAME**|**DBTYPE_WSTR**||文字セット名。 **NULL**プロバイダーが異なる文字セットをサポートしていない場合。|  
|**COLLATION_CATALOG**|**DBTYPE_WSTR**||照合順序が定義されているカタログ名。 **NULL**プロバイダーがカタログまたは各種照合順序をサポートしていない場合。|  
|**COLLATION_SCHEMA**|**DBTYPE_WSTR**||照合順序が定義されている、修飾されていないスキーマ名。 **NULL**プロバイダーはスキーマまたは各種照合順序をサポートしていない場合。|  
|**COLLATION_NAME**|**DBTYPE_WSTR**||照合順序名。 **NULL**プロバイダーは異なる照合順序をサポートしていない場合。|  
|**DOMAIN_CATALOG**|**DBTYPE_WSTR**||ドメインが定義されているカタログ名。 **NULL**プロバイダーがカタログまたはドメインをサポートしていない場合。|  
|**DOMAIN_SCHEMA**|**DBTYPE_WSTR**||ドメインが定義されている非修飾スキーマ名。 **NULL**プロバイダーはスキーマまたはドメインをサポートしていない場合。|  
|**ドメイン名**|**DBTYPE_WSTR**||ドメイン名。 **NULL**プロバイダーがドメインをサポートしていない場合。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||列に関して人が認識できる説明。 **NULL**かどうかは、列に関連付けられた説明はありません。|  
|**DISTRIBUTION_FLAG**|**DBTYPE_WSTR**||マイニング構造列の分布。<br /><br /> "**標準**"<br /><br /> "**LOG_NORM**AL"<br /><br /> "**UNIFORM**"|  
|**CONTENT_TYPE**|**DBTYPE_WSTR**||マイニング構造列のコンテンツの種類。<br /><br /> "**キー**"<br /><br /> "**DISCRETE**"<br /><br /> "**CONTINUOUS**"<br /><br /> "**DISCRETIZED (**[args]**)**"<br /><br /> "**ORDERED**"<br /><br /> "**SEQUENCE_TIME**"<br /><br /> "**CYCLICAL**"<br /><br /> "**確率**"<br /><br /> "**差異**"<br /><br /> "**STDEV**"<br /><br /> "**サポート**"<br /><br /> "**PROBABILITY_VARIANCE**"<br /><br /> "**PROBABILITY_STDEV**"|  
|**MODELING_FLAG**|**DBTYPE_WSTR**||モデリング フラグのコンマ区切りの一覧。 サポートされる唯一のフラグは、構造列の"**NOT NULL**"です。|  
|**IS_RELATED_TO_KEY**|**DBTYPE_BOOL**||この列がキーに関連しているかどうかを示すブール値。<br /><br /> **VARIANT_TRUE**場合、この列がキーに関連します。**VARIANT_FALSE**それ以外の場合。 キーが 1 つの列である場合、 **RELATED_ATTRIBUTE**フィールドは必要に応じてその列名を含めることがあります。|  
|**RELATED_ATTRIBUTE**|**DBTYPE_WSTR**||現在の列が関連している対象列の名前、または現在の列が特殊なプロパティである対象列の名前。|  
|**CONTAINING_COLUMN**|**DBTYPE_WSTR**||名前、**テーブル**この列を含む列。 **NULL**テーブルに列が含まれていない場合。|  
|**IS_POPULATED**|**DBTYPE_BOOL**||この列に一連の可能な値があるかどうかを示すブール値。<br /><br /> **TRUE**場合は、列が一連の使用可能な値です。**FALSE**、それ以外の場合。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DMSCHEMA_MINING_STRUCTURE_COLUMNS**行セットは、次の表の列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|省略可。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|省略可。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**COLUMN_NAME**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
