---
title: Property オブジェクト (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
author: rothja
ms.author: jroth
ms.openlocfilehash: d2f4a8b6cdeabcbab0802a0052ed697af70ef45a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759968"
---
# <a name="property-object-ado"></a>Property オブジェクト (ADO)
プロバイダーによって定義される ADO オブジェクトの動的特性を表します。  
  
## <a name="remarks"></a>Remarks  
 ADO オブジェクトには、組み込みと動的の2種類のプロパティがあります。  
  
 組み込みプロパティは ADO で実装されるプロパティで、構文を使用して、新しいオブジェクトですぐに使用でき `MyObject.Property` ます。 オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションには**プロパティ**オブジェクトとして表示されません。そのため、値を変更することはできますが、その特性を変更することはできません。  
  
 動的プロパティは、基になるデータプロバイダーによって定義され、適切な ADO オブジェクトの**properties**コレクションに表示されます。 たとえば、プロバイダー固有のプロパティは、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトがトランザクションをサポートするか更新するかを示します。 これらの追加のプロパティは、その**レコードセット**オブジェクトの**プロパティ**コレクション内の**プロパティ**オブジェクトとして表示されます。 動的プロパティは、コレクションを通じてのみ、または構文を使用して参照でき `MyObject.Properties(0)` `MyObject.Properties("Name")` ます。  
  
 どちらの種類のプロパティも削除できません。  
  
 動的**プロパティ**オブジェクトには、次の4つの組み込みプロパティがあります。  
  
-   [Name](../../../ado/reference/ado-api/name-property-ado.md)プロパティは、プロパティを識別する文字列です。  
  
-   [Type](../../../ado/reference/ado-api/type-property-ado.md)プロパティは、プロパティのデータ型を指定する整数です。  
  
-   [Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、プロパティ設定を含むバリアントです。 **Value**は、**プロパティ**オブジェクトの既定のプロパティです。  
  
-   [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティは、プロバイダー固有のプロパティの特性を示す long 型の値です。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Property オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
