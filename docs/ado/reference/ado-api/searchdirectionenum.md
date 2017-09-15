---
title: "SearchDirectionEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1ae30d042b6e1f4a3590cd8d3a46a636004aead8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
内のレコードの検索の方向を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|Description|  
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
