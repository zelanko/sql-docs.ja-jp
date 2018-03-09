---
title: "Close メソッド (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0607ee2889b32906968a5948138191d1fc67bb4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="close-method-ado-md"></a>Close メソッド (ADO MD)
開いているセルセットを閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>解説  
 使用して、**閉じる**を終了するメソッド、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトは、関連するすべてのデータを含む、関連付けられたデータを解放する[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)、または[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクト。 閉じる、**セルセット**メモリ; からは削除されませんプロパティの設定を変更し、後でもう一度開くことができます。 メモリからオブジェクトを完全になくすためには、オブジェクト変数を設定**Nothing**です。  
  
 後で呼び出すことができます、[開く](../../../ado/reference/ado-md-api/open-method-ado-md.md)を再度開くメソッド、**セルセット**同一または別の使用ソース文字列です。 中に、**セルセット**任意のプロパティを取得するか、基になるデータを参照するメソッドを呼び出す、オブジェクトが閉じられたか、メタデータには、エラーが生成されます。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [軸オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [セルのオブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [メンバー オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open メソッド (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [位置オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
