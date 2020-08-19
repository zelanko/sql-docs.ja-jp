---
description: Append メソッド (ADOX Procedures)
title: Append メソッド (ADOX Procedures) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
author: rothja
ms.author: jroth
ms.openlocfilehash: 8571790b596f037bb528df375c43c98b6b77c3a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440484"
---
# <a name="append-method-adox-procedures"></a>Append メソッド (ADOX Procedures)
[Procedures](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクションに新しい[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)オブジェクトを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 作成および追加するプロシージャの名前を示す **文字列** 値です。  
  
 *コマンド*  
 作成および追加するプロシージャを表す ADO [コマンド](../../../ado/reference/ado-api/command-object-ado.md) オブジェクト。  
  
## <a name="remarks"></a>解説  
 **コマンド**オブジェクトで指定された名前と属性を使用して、データソースに新しいプロシージャを作成します。  
  
 ユーザーが指定したコマンドテキストがプロシージャではなくビューを表している場合、その動作は使用されているプロバイダーによって異なります。 プロバイダーがコマンドの永続化をサポートしていない場合、 **Append**は失敗します。  
  
> [!NOTE]
>  OLE DB Provider for Microsoft Jet を使用する場合、 **Procedures** collection **Append**メソッドを使用すると、*コマンド*パラメーターで**プロシージャ**ではなく**ビュー**を指定できます。 **ビュー**がデータソースに追加され、**プロシージャ**コレクションに追加されます。 **追加**後、**プロシージャ**コレクションと**ビュー**コレクションが更新されると、その**ビュー**は**procedures**コレクションに含まれなくなり、 **views**コレクションに表示されます。  
  
## <a name="applies-to"></a>適用対象  
 [Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Procedures Append メソッドの例 (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append メソッド (ADOX Columns)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Indexes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX Keys)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
