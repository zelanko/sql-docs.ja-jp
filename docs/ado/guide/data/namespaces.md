---
title: "名前空間 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: namespaces in ADO
ms.assetid: efff5569-db52-451d-a039-2e74870534da
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b5921d1c91ee326810041c612097c41e9e099e2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="namespaces"></a>名前空間
ADO での XML 永続形式では、次の 4 つの名前空間を使用します。  
  
## <a name="remarks"></a>解説  
 ADO での XML 永続形式では、次の 4 つの名前空間を使用します。  
  
|Prefix|Description|  
|------------|-----------------|  
|s|要素と現在のレコード セットのスキーマを定義する属性を含む「XML データ」の名前空間を参照します。|  
|dt|データ型の定義の仕様を参照します。|  
|rs|名前空間を含む要素と ADO レコード セットのプロパティに固有の属性と属性を表します。|  
|z|現在の行セットのスキーマを参照します。|  
  
 クライアントの仕様で定義されている、独自のタグをこれらの名前空間に追加しないでください。 たとえば、クライアントと名前空間を定義する必要があります"urn: スキーマ-microsoft-com:rowset"と"rs: MyOwnTag"などのものを書き込み、。 名前空間に関する詳細についてを参照してください、[勧告の XML での W3C 名前空間](http://www.w3.org/TR/REC-xml-names/)です。  
  
> [!IMPORTANT]
>  スキーマのタグの ID は"RowsetSchema、"である必要があり。、現在の行セットのスキーマを参照するために使用する名前空間が"#RowsetSchema"をポイントする必要があります。  
  
 注意してください、名前空間のプレフィックス、コロンと等号の間の部分 — は任意です。  
  
```  
xmlns:rs="urn:schemas-microsoft-com:rowset"  
```  
  
 ユーザーは、この名前の使用は、XML ドキュメント全体で一貫している限り、任意の名前を指定するを定義できます。 ADO は、"s"、"rs"「dt」常に書き込み、"z"が、これらのプレフィックス名されませんハードコーディングされたコンポーネントを読み込み中にします。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
