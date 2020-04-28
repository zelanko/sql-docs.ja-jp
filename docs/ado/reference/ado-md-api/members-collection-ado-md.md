---
title: Members コレクション (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79394abee5b12bb10f34a34e882d2ac0562722fe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949430"
---
# <a name="members-collection-ado-md"></a>Members コレクション (ADO MD)
レベルまたは軸に沿った位置からの[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトを格納します。  
  
## <a name="remarks"></a>Remarks  
 **メンバー**コレクションは、次の種類のメンバーを格納するために使用されます。  
  
-   キューブ内のレベルを構成するメンバー。 これらは、 [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトの**Members**コレクションに含まれています。 たとえば、[多次元スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)からサンプルを使用すると、国レベルの4つのメンバーがカナダ、USA、英国、およびドイツになります。  
  
-   階層内の特定のメンバーの子であるメンバー。 これらのメンバーは、親**メンバー**オブジェクトの[Children](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティによって返されます。 たとえば、同じサンプルをもう一度使用した場合、カナダのメンバーの2つの子はカナダ-東部、カナダ西部です。  
  
-   [セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)の軸に沿って特定の位置を定義するメンバー。 例として、セルセットを使用して[多次元データを操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)する場合、x 軸の最初の位置の2つのメンバーはバレンタインと Seattle です。 これらのメンバーは、 [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクトの**members**コレクションに含まれています。  
  
 **メンバー**は、標準の ADO コレクションです。 コレクションのプロパティとメソッドを使用して、次の操作を実行できます。  
  
-   [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、コレクション内のオブジェクトの数を取得します。  
  
-   既定の[Item](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して、コレクションからオブジェクトを返します。  
  
-   [更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを使用して、プロバイダーからコレクション内のオブジェクトを更新します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Members の例 (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
