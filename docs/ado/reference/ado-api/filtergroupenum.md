---
title: FilterGroupEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97add08a1d656e8c163600bb0ea8dda7fca264b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932642"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
レコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)からフィルター選択するレコードのグループを指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|最後の[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、 [Resync](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)呼び出しの影響を受けたレコードのみを表示するためのフィルター。|  
|**Adfilter衝突レコード**|5|前回のバッチ更新に失敗したレコードを表示するためのフィルター。|  
|**adFilterFetchedRecords**|3|現在のキャッシュ内のレコードを表示するためのフィルター。つまり、データベースからレコードを取得するための最後の呼び出しの結果です。|  
|**adFilterNone**|0|現在のフィルターを削除し、表示するすべてのレコードを復元します。|  
|**adFilterPendingRecords**|1|サーバーにまだ送信されていない、変更されたレコードのみを表示するためのフィルター。 バッチ更新モードにのみ適用されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums AFFECTEDRECORDS|  
|AdoEnums を記録します。|  
|AdoEnums レコードのグループ化|  
|AdoEnums. FilterGroup|  
|AdoEnums のフィルター|  
  
## <a name="applies-to"></a>適用対象  
 [Filter プロパティ](../../../ado/reference/ado-api/filter-property.md)
