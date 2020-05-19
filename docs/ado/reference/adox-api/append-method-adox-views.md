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
author: rothja
ms.author: jroth
ms.openlocfilehash: 540ff52141139f4748cb2cd4c8979f5f8b55b230
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764003"
---
# <a name="append-method-adox-views"></a>Append メソッド (ADOX Views)
新しい[ビュー](../../../ado/reference/adox-api/view-object-adox.md)オブジェクトを作成し、 [Views](../../../ado/reference/adox-api/views-collection-adox.md)コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 作成するビューの名前を指定する**文字列**値。  
  
 *コマンド*  
 作成するビューを表す ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="remarks"></a>Remarks  
 **コマンド**オブジェクトで指定された名前と属性を使用して、データソースに新しいビューを作成します。  
  
 ユーザーが指定したコマンドテキストがビューではなくプロシージャを表している場合、その動作はプロバイダーに依存します。 プロバイダーがコマンドの永続化をサポートしていない場合、 **Append**は失敗します。  
  
> [!NOTE]
>  OLE DB Provider for Microsoft Jet を使用する場合、 **Views** collection **Append**メソッドを使用すると、*コマンド*パラメーターで**ビュー**ではなく**プロシージャ**を指定できます。 **プロシージャ**がデータソースに追加され、 **Views**コレクションに追加されます。 **追加**後、**プロシージャ**と**ビュー**のコレクションが更新されると、その**プロシージャ**は**views**コレクションに含まれなくなり、 **procedures**コレクションに表示されます。  
  
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
