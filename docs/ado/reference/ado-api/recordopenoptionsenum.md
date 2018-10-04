---
title: RecordOpenOptionsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab648d7fe60a27d36e55cd3d859d0a8c442eef50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644814"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
開くのためのオプションを指定します、[レコード](../../../ado/reference/ado-api/record-object-ado.md)します。 使用して、これらの値を組み合わせることができますか。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|フィールドに関連付けられているプロバイダーに示します、**レコード**最初に、取得する必要がありませんが、フィールドにアクセスする最初の試行で取得できます。 ない場合、このフラグで示される、既定の動作がすべて取得するには、**レコード**フィールド オブジェクトします。|  
|**adDelayFetchStream**|0x4000|既定のストリームに関連付けられているプロバイダーに示します、**レコード**最初に取得する必要がありません。 関連付けられている既定のストリームを取得するがない場合、このフラグで示された既定の動作は、**レコード**オブジェクト。|  
|**adOpenAsync**|0x1000|示します、**レコード**オブジェクトは非同期モードで開きます。|  
|**adOpenExecuteCommand**|0x10000|ソース文字列が実行されるコマンド テキストが含まれていることを示します。 この値は、 **adCmdText**オプション**Recordset.Open**します。|  
|**adOpenRecordUnspecified**|-1|既定値です。 オプションが指定されていないことを示します。|  
|**adOpenOutput**|0x800000|ソースは、実行可能スクリプトを含むノードを指している場合は、ことを示します (など、します。ASP ページの場合)、開かれた**レコード**実行されたスクリプトの結果が含まれます。 この値はコレクションではないレコードのみです。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 これらの定数には、ADO と WFC 対応はありません。  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
