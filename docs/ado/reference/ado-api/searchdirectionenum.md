---
title: Searchdirection 列挙型 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8926e932317096cb3891cc8c480164268751cea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916998"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
レコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)内のレコード検索の方向を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|後方に検索し、**レコードセット**の先頭で停止します。 一致するものが見つからない場合、レコードポインターは[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)に配置されます。|  
|**adSearchForward**|1 で保護されたプロセスとして起動されました|**レコードセット**の末尾で停止します。 一致するものが見つからない場合、レコードポインターは[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)に位置します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums.|  
|AdoEnums の順方向|  
  
## <a name="applies-to"></a>適用対象  
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
