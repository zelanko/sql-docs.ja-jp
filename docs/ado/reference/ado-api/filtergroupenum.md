---
description: FilterGroupEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7552eb4b069b2cd2adc33e0bff25f23d918468c2
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775291"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
レコード [セット](./recordset-object-ado.md)からフィルター選択するレコードのグループを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|最後の [Delete](./delete-method-ado-recordset.md)、 [Resync](./resync-method.md)、 [UpdateBatch](./updatebatch-method.md)、または [CancelBatch](./cancelbatch-method-ado.md) 呼び出しの影響を受けたレコードのみを表示するためのフィルター。|  
|**Adfilter衝突レコード**|5|前回のバッチ更新に失敗したレコードを表示するためのフィルター。|  
|**adFilterFetchedRecords**|3|現在のキャッシュ内のレコードを表示するためのフィルター。つまり、データベースからレコードを取得するための最後の呼び出しの結果です。|  
|**adFilterNone**|0|現在のフィルターを削除し、表示するすべてのレコードを復元します。|  
|**adFilterPendingRecords**|1|サーバーにまだ送信されていない、変更されたレコードのみを表示するためのフィルター。 バッチ更新モードにのみ適用されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums AFFECTEDRECORDS|  
|AdoEnums を記録します。|  
|AdoEnums レコードのグループ化|  
|AdoEnums. FilterGroup|  
|AdoEnums のフィルター|  
  
## <a name="applies-to"></a>適用対象  
 [Filter プロパティ](./filter-property.md)