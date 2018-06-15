---
title: Append メソッド (ADOX プロシージャ) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: bc5721f8806481de872d0c3e1de7d47a3720dfa9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284861"
---
# <a name="append-method-adox-procedures"></a>Append メソッド (ADOX プロシージャ)
新しく追加[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)オブジェクトを[プロシージャ](../../../ado/reference/adox-api/procedures-collection-adox.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Name*  
 A**文字列**プロシージャを作成し、追加の名前を指定する値。  
  
 *Command*  
 ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)を作成し、追加の手順を表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
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
