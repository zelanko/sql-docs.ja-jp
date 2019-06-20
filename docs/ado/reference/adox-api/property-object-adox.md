---
title: オブジェクトのプロパティ (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2f07d14d30f3fd87be8fc61552716a931ed86d68
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705957"
---
# <a name="property-object-adox"></a>Property オブジェクト (ADOX)
ADOX オブジェクトの特性を表します。  
  
## <a name="remarks"></a>コメント  
 ADOX オブジェクトは、2 種類のプロパティを設定します。 組み込みおよび動的な。  
  
 組み込みのプロパティは、MyObject.Property 構文を使用して、すべての新しいオブジェクトにすぐに利用できるこれらのプロパティです。 オブジェクトのプロパティ オブジェクトとして表示されない[プロパティ コレクション](../../../ado/reference/ado-api/properties-collection-ado.md)ので、その値を変更できますが、その特性を変更することはできません。  
  
 動的プロパティは基になるデータ プロバイダーによって定義され ADOX の適切なオブジェクトのプロパティのコレクション。  動的プロパティは、MyObject.Properties(0) または MyObject.Properties("Name") 構文を使用して、コレクションのみを参照できます。  
  
 プロパティのいずれかの種類を削除することはできません。  
  
 動的プロパティ オブジェクトには、独自の 4 つの組み込みプロパティがあります。  
  
 [名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティは、プロパティを識別する文字列。  
  
 [型](../../../ado/reference/ado-api/type-property-ado.md)プロパティは、プロパティのデータ型を指定する整数。  
  
 [値](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、プロパティの設定を含んでいるバリアント。 値は、プロパティ オブジェクトの既定のプロパティです。  
  
 [属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティは、プロバイダーに固有のプロパティの特性を示す long 値。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [ADOX Property オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
