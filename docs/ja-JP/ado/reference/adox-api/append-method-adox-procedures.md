---
title: Append メソッド (ADOX プロシージャ) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5b4cb7f58f82113dbefd0928e3450059cf01d5d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="append-method-adox-procedures"></a>Append メソッド (ADOX プロシージャ)
新しく追加[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)オブジェクトを[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 A**文字列**プロシージャを作成し、追加の名前を指定する値。  
  
 *Command*  
 ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を作成し、追加の手順を表すオブジェクト。  
  
## <a name="remarks"></a>解説  
 指定した属性と名前を持つデータ ソースに新しいプロシージャを作成、**コマンド**オブジェクト。  
  
 ユーザーが指定したコマンド テキストを表す場合、プロシージャではなく、ビュー、動作は、使用されているプロバイダーによって異なります。 **追加**プロバイダーは永続的なコマンドをサポートしていない場合は失敗します。  
  
> [!NOTE]
>  For Microsoft Jet OLE DB プロバイダーを使用する場合、**プロシージャ**コレクション**Append**を指定するメソッドを使用できる、**ビュー**ではなく、 **プロシージャ**で、*コマンド*パラメーター。 **ビュー**がデータ ソースに追加されに追加されます、**プロシージャ**コレクション。 後に、 **Append**場合、**プロシージャ**と**ビュー**コレクションが更新されると、**ビュー** でしなくなる**プロシージャ**コレクションに表示されます、**ビュー**コレクション。  
  
## <a name="applies-to"></a>適用対象  
 [Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>参照  
 [プロシージャは、メソッドの例 (VB) を追加します。](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append メソッド (ADOX 列)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX グループ)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX インデックス)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append メソッド (ADOX キー)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append メソッド (ADOX ユーザー)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append メソッド (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)
