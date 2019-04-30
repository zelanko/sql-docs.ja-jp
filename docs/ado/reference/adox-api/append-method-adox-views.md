---
title: Append メソッド (ADOX Views) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 584c3d0144197425b307f2d4a04bd8a09f27a36c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184219"
---
# <a name="append-method-adox-views"></a>Append メソッド (ADOX Views)
新たに作成[ビュー](../../../ado/reference/adox-api/view-object-adox.md)オブジェクトに追加され、[ビュー](../../../ado/reference/adox-api/views-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 A**文字列**を作成するビューの名前を指定する値。  
  
 *Command*  
 ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を作成するビューを表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
 指定された属性と名前を持つデータ ソースに新しいビューを作成、**コマンド**オブジェクト。  
  
 ビューではなく、プロシージャをユーザーが指定するコマンド テキストを表している場合、動作は、プロバイダーによって異なります。 **追加**プロバイダーは永続的なコマンドをサポートしていない場合は失敗します。  
  
> [!NOTE]
>  Microsoft Jet OLE DB Provider を使用する場合、**ビュー**コレクション**Append**メソッドには、指定することが、**プロシージャ**なく**ビュー**で、*コマンド*パラメーター。 **プロシージャ**がデータ ソースに追加されに追加されます、**ビュー**コレクション。 後に、 **Append**場合、**プロシージャ**と**ビュー**コレクションが更新されると、**プロシージャ**でしなくなる**ビュー**コレクションに表示されますが、**プロシージャ**コレクション。  
  
## <a name="applies-to"></a>適用対象  
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [Views Append メソッドの例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append メソッド (ADOX Columns)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Indexes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX Keys)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX Procedures)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append メソッド (ADOX Tables)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)
