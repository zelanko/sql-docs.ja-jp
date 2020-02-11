---
title: RecordTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df70838b7986993459df4f37af8b7043626a5d7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931262"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの種類を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|*単純な*レコードを示します (子ノードは含まれません)。|  
|**adCollectionRecord**|1 で保護されたプロセスとして起動されました|*コレクション*レコード (子ノードを含む) を示します。|  
|**adRecordUnknown**|-1|この**レコード**の型が不明であることを示します。|  
|**adStructDoc**|2|COM 構造化ドキュメントを表す特別な種類の*コレクション*レコードを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [RecordType プロパティ (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
