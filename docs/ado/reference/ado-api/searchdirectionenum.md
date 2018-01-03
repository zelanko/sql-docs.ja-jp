---
title: "SearchDirectionEnum |Microsoft ドキュメント"
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
f1_keywords: SearchDirectionEnum
helpviewer_keywords: SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 647dc72033d44c9b2b015506875b6939e531a8e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
内のレコードの検索の方向を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|先頭に停止する旧バージョンと、検索、 **Recordset**です。 一致が見つからない場合、レコード ポインターは[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)です。|  
|**adSearchForward**|@shouldalert|検索を転送するの末尾に移動する、 **Recordset**です。 一致が見つからない場合、レコード ポインターは[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)です。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>適用対象  
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
