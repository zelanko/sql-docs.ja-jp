---
description: Key オブジェクト (ADOX)
title: Key オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: rothja
ms.author: jroth
ms.openlocfilehash: d622adac64a37d956fc71ee1399c2d147b2f993a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439864"
---
# <a name="key-object-adox"></a>Key オブジェクト (ADOX)
データベーステーブルの主キー、外部キー、または一意キーフィールドを表します。  
  
## <a name="remarks"></a>解説  
 次のコードでは、新しい **キー**が作成されます。  
  
```  
Dim obj As New Key  
```  
  
 **キー**オブジェクトのプロパティとコレクションを使用すると、次のことができます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してキーを識別します。  
  
-   [Type](../../../ado/reference/adox-api/type-property-key-adox.md)プロパティを使用して、キーがプライマリ、外部、または一意であるかどうかを確認します。  
  
-   [Columns](../../../ado/reference/adox-api/columns-collection-adox.md)コレクションを使用して、キーのデータベース列にアクセスします。  
  
-   関連テーブルの名前を "関連付け [テーブル](../../../ado/reference/adox-api/relatedtable-property-adox.md) " プロパティと共に指定します。  
  
-   [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md)プロパティと[UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md)プロパティを使用して、主キーの削除または更新に対して実行されるアクションを確認します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Key オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Keys Append メソッド、Key Type、UpdateRule プロパティの例 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
