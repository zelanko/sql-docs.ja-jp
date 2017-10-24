---
title: "DefinedSize プロパティ |Microsoft ドキュメント"
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
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 650eb80c6d4301c1a5881b3348dc2bbef9269fb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="definedsize-property"></a>DefinedSize プロパティ
データ容量を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**フィールド オブジェクトのデータ型によって異なります。 表示されるフィールドの定義のサイズを反映した値[型](../../../ado/reference/ado-api/type-property-ado.md)詳細についてはします。 固定長データ型を使用するフィールドの場合は、戻り値は、バイト単位でのデータ型のサイズです。 可変長データ型を使用するフィールドの場合これは、次のいずれかです。  
  
1.  文字内のフィールドの最大長 (の**それぞれ**と**adVarWChar**) またはバイト数 (の**adVarBinary**、および**adVarNumeric**) フィールドに定義された長さがある場合。 たとえば、 **adVarChar(5)**フィールドが 5 の最大長。  
  
2.  文字データ型の最大長 (の**ファミリ**と**adWChar**) またはバイト数 (の**adBinary**と**adNumeric**) 場合、フィールドには、定義された長さがありません。  
  
3.  ~ 0 (ビット演算子、値は 0 以外のすべてのビットが 1 に設定されます)、フィールドもデータ型も定義されている最大長である場合。  
  
4.  長さがないデータ型、これに設定されている ~ 0 (ビット演算子、値は 0 以外のすべてのビットが 1 に設定されます)。  
  
## <a name="remarks"></a>解説  
 使用して、 **DefinedSize**のデータ容量を決定するプロパティ、**フィールド**オブジェクト。  
  
 **DefinedSize**と[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)プロパティは異なります。 たとえば、**フィールド**の宣言された型とオブジェクト**それぞれ**と**DefinedSize** 50、1 つの文字を含むのプロパティの値。 **ActualSize**返さプロパティの値は 1 つの文字の長さ (バイト単位)。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [ActualSize と DefinedSize プロパティの例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize と DefinedSize プロパティの例 (vc++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [ActualSize プロパティ (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)

