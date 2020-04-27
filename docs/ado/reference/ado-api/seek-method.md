---
title: Seek メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e2ee81ac2ede53eb4fdbcfe8d3b5987db96f1ad
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917012"
---
# <a name="seek-method"></a>Seek メソッド
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)のインデックスを検索して、指定した値と一致する行をすばやく検索し、現在の行の位置をその行に変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>パラメーター  
 *KeyValues*  
 **バリアント**値の配列。 インデックスは1つ以上の列で構成され、配列には対応する各列と比較するための値が含まれます。  
  
 *SeekOption*  
 インデックスの列とそれに対応する*Keyvalues*の間で行われる比較の種類を指定する[seekenum](../../../ado/reference/ado-api/seekenum.md)値。  
  
## <a name="remarks"></a>Remarks  
 基になるプロバイダーが**レコードセット**オブジェクトのインデックスをサポートしている場合は、 [Index](../../../ado/reference/ado-api/index-property.md)プロパティと共に**Seek**メソッドを使用します。 [サポート](../../../ado/reference/ado-api/supports-method.md)**(adseek)** メソッドを使用して、基になるプロバイダーが**Seek**をサポートするかどうかを判断し、**サポート (adseek)** メソッドを使用して、プロバイダーがインデックスをサポートしているかどうかを判断します。 (たとえば、 [Microsoft Jet の OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)では、 **Seek**および**Index**がサポートされています)。  
  
 **Seek**が目的の行を見つけられない場合、エラーは発生せず、行は**レコードセット**の末尾に配置されます。 このメソッドを実行する前に、 **index**プロパティを目的のインデックスに設定します。  
  
 このメソッドは、サーバー側のカーソルでのみサポートされています。 **レコードセット**オブジェクトの[カーソル位置](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティ値が**adUseClient**の場合、シークはサポートされません。  
  
 このメソッドは、**レコードセット**オブジェクトが[commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値**adcmdtabledirect**を使用して開かれている場合にのみ使用できます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Seek メソッドと Index プロパティの例 (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Seek メソッドおよび Index プロパティの例 (VC + +)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index プロパティ](../../../ado/reference/ado-api/index-property.md)
