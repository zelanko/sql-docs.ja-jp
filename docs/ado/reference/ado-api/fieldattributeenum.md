---
title: "FieldAttributeEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: FieldAttributeEnum
helpviewer_keywords: FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b5a1783b5906b53f1c092418ea22d2cbc0f51e6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
1 つまたは複数の属性を指定します、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|プロバイダーはフィールドの値がキャッシュされると、キャッシュからその後の読み込みを行うことを示します。|  
|**adFldFixed**|0x10|フィールドが固定長のデータが含まれていることを示します。|  
|**adFldIsChapter**|0x2000|フィールドにこの親フィールドに関連する特定の子レコード セットを指定します、章の値が含まれていることを示します。 通常章フィールドは、データの整形またはフィルターで使用されます。|  
|**adFldIsCollection**|0x40000|フィールドがレコードによって表されるリソースがテキスト ファイルなどの単純なリソースではなく、フォルダーなど、その他のリソースのコレクションであるを指定することを示します。|  
|**adFldKeyColumn**|0x8000|列の主キーの一部またはすべてのフィールドが指定されることを示します。|  
|**adFldIsDefaultStream**|0x20000|フィールドにレコードによって表されるリソースの既定のストリームが含まれていることを示します。 たとえば、既定のストリームは、ルートの URL を指定すると自動的に提供される Web サイト上のルート フォルダーの HTML コンテンツを指定できます。|  
|**adFldIsNullable**|0x20|フィールドが null 値を受け入れることを示します。|  
|**adFldIsRowURL**|0x10000|フィールドに、リソース レコードによって表されるデータ ストアからの名前を示す URL が含まれていることを示します。|  
|**adFldLong**|0x80|フィールドがフィールド長のバイナリであることを示します。 使用できることを示す、 [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)と[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)メソッドです。|  
|**adFldMayBeNull**|0x40|フィールドの null 値を読み取ることができますを示します。|  
|**adFldMayDefer**|0x2|フィールドが遅延していることを示します: つまり、フィールドの値は、レコード全体ですが明示的にアクセスする場合にのみ、データ ソースから取得されません。|  
|**adFldNegativeScale**|0x4000|フィールドが負の値の小数点以下桁数の値をサポートする列の数値の値を表すことを示します。 小数点以下桁数がで指定された、 [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)プロパティです。|  
|**adFldRowID**|0x100|フィールドに書き込むことができません (など、レコード番号、一意の識別子など)、行を識別する以外の意味のある値を持たないを永続的な行識別子が含まれていることを示します。|  
|**adFldRowVersion**|0x200|フィールドに何らか更新プログラムを追跡するために使用される日付または時刻のタイムスタンプにはが含まれていることを示します。|  
|**adFldUnknownUpdatable**|0x8|プロバイダーが、フィールドを書き込むことができるかどうかを判断できないことを示します。|  
|**adFldUnspecified**|-1 0 xffffffff|プロバイダーに、フィールドの属性が指定されていないことを示します。|  
|**adFldUpdatable**|0x4|フィールドに記述できることを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.FieldAttribute.CACHEDEFERRED|  
|AdoEnums.FieldAttribute.FIXED|  
|AdoEnums.FieldAttribute.ISNULLABLE|  
|AdoEnums.FieldAttribute.LONG|  
|AdoEnums.FieldAttribute.MAYBENULL|  
|AdoEnums.FieldAttribute.MAYDEFER|  
|AdoEnums.FieldAttribute.NEGATIVESCALE|  
|AdoEnums.FieldAttribute.ROWID|  
|AdoEnums.FieldAttribute.ROWVERSION|  
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE|  
|AdoEnums.FieldAttribute.UNSPECIFIED|  
|AdoEnums.FieldAttribute.UPDATABLE|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Append メソッド (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Attributes プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|
