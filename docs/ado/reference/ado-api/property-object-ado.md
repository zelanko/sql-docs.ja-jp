---
title: "プロパティのオブジェクト (ADO) |Microsoft ドキュメント"
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
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4a0c5a1217cb8143a0b275ea3d0c31e16b7d1cd1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="property-object-ado"></a>プロパティのオブジェクト (ADO)
プロバイダーによって定義されている ADO オブジェクトの動的な特性を表します。  
  
## <a name="remarks"></a>解説  
 ADO オブジェクトが 2 種類のプロパティを設定します。 組み込みと動的です。  
  
 組み込みのプロパティは、これらのプロパティは、ADO では実装されていると、すぐに利用できる、新しいオブジェクトを使用して、`MyObject.Property`構文です。 としては表示されません**プロパティ**オブジェクトの内のオブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション、ため、その値を変更できますが、その特性を変更することはできません。  
  
 動的プロパティは、基になるデータ プロバイダーによって定義されに表示されます、**プロパティ**該当する ADO オブジェクトのコレクション。 たとえば、プロバイダーに固有のプロパティを示す場合、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトは、トランザクションや更新をサポートしています。 これらの追加プロパティとして表示されます**プロパティ**を内のオブジェクト**レコード セット**オブジェクトの**プロパティ**コレクション。 動的なプロパティは、コレクションを通じてのみ参照できますを使用して、`MyObject.Properties(0)`または`MyObject.Properties("Name")`構文です。  
  
 プロパティのいずれかの種類を削除することはできません。  
  
 動的な**プロパティ**オブジェクトには、独自の 4 つの組み込みプロパティ。  
  
-   [名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティは、プロパティを識別する文字列。  
  
-   [型](../../../ado/reference/ado-api/type-property-ado.md)プロパティは、プロパティのデータ型を指定する整数。  
  
-   [値](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、プロパティの設定を含んでいるバリアント。 **値**の既定のプロパティは、**プロパティ**オブジェクト。  
  
-   [属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティは、プロバイダーに固有のプロパティの特性を示す long 値です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
