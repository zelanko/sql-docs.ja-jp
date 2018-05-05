---
title: Seek メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 59dcdd3426c39449b3d2348218aa7794a75c0474
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="seek-method"></a>Seek メソッド
インデックスを検索、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)に指定した値に一致する行に現在の行位置を変更した行をすばやく検索します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>パラメーター  
 *KeyValues*  
 配列**バリアント**値。 インデックスは 1 つまたは複数の列と配列に対応する各列に対して比較する値が含まれています。  
  
 *SeekOption*  
 A [SeekEnum](../../../ado/reference/ado-api/seekenum.md)できるは、インデックスの列と、対応するための比較の種類を指定する値*keyvalues とも*します。  
  
## <a name="remarks"></a>解説  
 使用して、**シーク**メソッドと組み合わせて、[インデックス](../../../ado/reference/ado-api/index-property.md)基になるプロバイダーのインデックスをサポートする場合は、プロパティ、 **Recordset**オブジェクト。 使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** 基になるプロバイダーがサポートしているかどうかを判断するメソッド**シーク**、および**Supports(adIndex)** プロバイダーはインデックスをサポートするかどうかを判断するメソッドです。 (たとえば、 [OLE DB Provider for Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)をサポートしている**シーク**と**インデックス**)。  
  
 場合**シーク**は検索対象の行では、エラーはありませんが発生すると、およびその行がの末尾に配置されている、 **Recordset**です。 設定、**インデックス**にこのメソッドを実行する前に目的のインデックスのプロパティです。  
  
 このメソッドは、サーバー側のカーソルでのみサポートされます。 シークときはサポートされていません、 **Recordset**オブジェクトの[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティの値が**adUseClient**です。  
  
 このメソッドは、必ず際に使用される、 **Recordset**でオブジェクトが開かれた、 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値**adCmdTableDirect**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドとインデックスのプロパティの例 (VB) にシークします。](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [メソッドとインデックスのプロパティの例 (vc++) にシークします。](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index プロパティ](../../../ado/reference/ado-api/index-property.md)
