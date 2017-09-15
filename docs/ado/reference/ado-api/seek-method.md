---
title: "Seek メソッド |Microsoft ドキュメント"
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
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d401bca51d735b2d0d633716cee732ad2ab9a086
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="seek-method"></a>Seek メソッド
インデックスを検索、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)に指定した値に一致する行に現在の行位置を変更した行をすばやく検索します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Keyvalues とも*  
 配列**バリアント**値。 インデックスは 1 つまたは複数の列と配列に対応する各列に対して比較する値が含まれています。  
  
 *SeekOption*  
 A [SeekEnum](../../../ado/reference/ado-api/seekenum.md)できるは、インデックスの列と、対応するための比較の種類を指定する値*keyvalues とも*します。  
  
## <a name="remarks"></a>解説  
 使用して、**シーク**メソッドと組み合わせて、[インデックス](../../../ado/reference/ado-api/index-property.md)基になるプロバイダーのインデックスをサポートする場合は、プロパティ、 **Recordset**オブジェクト。 使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)**(adSeek)**基になるプロバイダーがサポートしているかどうかを判断するメソッド**シーク**、および**Supports(adIndex)**プロバイダーはインデックスをサポートするかどうかを判断するメソッドです。 (たとえば、 [OLE DB Provider for Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)をサポートしている**シーク**と**インデックス**)。  
  
 場合**シーク**は検索対象の行では、エラーはありませんが発生すると、およびその行がの末尾に配置されている、 **Recordset**です。 設定、**インデックス**にこのメソッドを実行する前に目的のインデックスのプロパティです。  
  
 このメソッドは、サーバー側のカーソルでのみサポートされます。 シークときはサポートされていません、 **Recordset**オブジェクトの[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティの値が**adUseClient**です。  
  
 このメソッドは、必ず際に使用される、 **Recordset**でオブジェクトが開かれた、 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値**adCmdTableDirect**です。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドとインデックスのプロパティの例 (VB) にシークします。](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [メソッドとインデックスのプロパティの例 (vc++) にシークします。](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index プロパティ](../../../ado/reference/ado-api/index-property.md)
