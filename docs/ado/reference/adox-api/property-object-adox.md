---
title: Property オブジェクト (ADOX) |Microsoft Docs
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
ms.openlocfilehash: b7911608970e9860d7eddcf3e83156ac99645c3f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965393"
---
# <a name="property-object-adox"></a>Property オブジェクト (ADOX)
ADOX オブジェクトの特性を表します。  
  
## <a name="remarks"></a>Remarks  
 ADOX オブジェクトには、組み込みと動的の2種類のプロパティがあります。  
  
 組み込みプロパティは、新しいオブジェクトですぐに使用できるプロパティで、MyObject 構文を使用します。 オブジェクトの[プロパティコレクション](../../../ado/reference/ado-api/properties-collection-ado.md)にはプロパティオブジェクトとして表示されません。そのため、値を変更することはできますが、その特性を変更することはできません。  
  
 動的プロパティは、基になるデータプロバイダーによって定義され、適切な ADOX オブジェクトの Properties コレクションに表示されます。  動的プロパティを参照できるのは、コレクションを介して、MyObject (0) または MyObject. Properties ("Name") 構文を使用する場合のみです。  
  
 どちらの種類のプロパティも削除できません。  
  
 動的プロパティオブジェクトには、次の4つの組み込みプロパティがあります。  
  
 [Name](../../../ado/reference/ado-api/name-property-ado.md)プロパティは、プロパティを識別する文字列です。  
  
 [Type](../../../ado/reference/ado-api/type-property-ado.md)プロパティは、プロパティのデータ型を指定する整数です。  
  
 [Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、プロパティ設定を含むバリアントです。 Value は、プロパティオブジェクトの既定のプロパティです。  
  
 [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティは、プロバイダー固有のプロパティの特性を示す long 型の値です。  
  
 ここでは、次のトピックについて説明します。  
  
-   [ADOX Property オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
