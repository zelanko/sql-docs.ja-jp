---
title: "ParentURL プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eca04999eece256ef22503c4d227ffcec297c79a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="parenturl-property-ado"></a>ParentURL プロパティ (ADO)
親を指す絶対 URL 文字列を示す[レコード](../../../ado/reference/ado-api/record-object-ado.md)、現在の**レコード**オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**文字列**を親の URL を示す値**レコード**です。  
  
## <a name="remarks"></a>解説  
 **ParentURL**プロパティを開くには使用されているソースに依存、**レコード**オブジェクト。 たとえば、**レコード**によって参照されるディレクトリの相対パス名を含むソースで開くことが、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティです。  
  
 たとえば、"first"の下のフォルダーは「秒」含まれています。 開く、**レコード**次の構文を使用してオブジェクト。  
  
```  
record.ActiveConnection = "http://first"  
record.Open "second"  
```  
  
 値、 `the` **ParentURL**プロパティは`"http://first"`と同じ**ActiveConnection**です。  
  
 ソースすることもできます絶対 URL など、`"http://first/second"`です。 **ParentURL**プロパティは、 `"http://first"`、その上のレベル`"second"`です。  
  
 このプロパティは、場合、null 値にすることがあります。  
  
-   現在のオブジェクトの親が存在しません。たとえば場合、**レコード**オブジェクトは、ディレクトリのルートを表します。  
  
-   **レコード**オブジェクトは、URL で指定することはできません、エンティティを表します。  
  
 このプロパティは読み取り専用です。  
  
> [!NOTE]
>  このプロパティはなど、ドキュメントのソース プロバイダーによってサポートのみ、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[レコードとプロバイダー提供フィールド](../../../ado/guide/data/records-and-provider-supplied-fields.md)です。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
> [!NOTE]
>  現在のレコードが ADO からのデータ レコードを含むかどうか**レコード セット**へのアクセス、 **ParentURL**プロパティ URL が可能なないことを示す、実行時エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
