---
title: SearchDirectionEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f6cba75e0e4a2bf164c36f65c9e5fe58d81b1e4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281571"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
内のレコードの検索の方向を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|先頭に停止する旧バージョンと、検索、 **Recordset**です。 一致が見つからない場合、レコード ポインターは[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)です。|  
|**adSearchForward**|1|検索を転送するの末尾に移動する、 **Recordset**です。 一致が見つからない場合、レコード ポインターは[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)です。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>適用対象  
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
