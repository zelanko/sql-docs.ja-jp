---
title: "手順 4: 設定の詳細 テキスト ボックス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 512ad22b6529adcf065cacb219d1f0acc025c306
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-4-populate-the-details-text-box"></a>手順 4: 設定の詳細 テキスト ボックス
詳細テキスト ボックスに入力、という名前の新しいサブルーチンを作成**recFields**し、次のコードを挿入します。  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 このコードを取得し`lstDetails`に渡される単純なレコードの値とフィールドと`recFields`です。 リソースがテキスト ファイルの場合は、テキスト ストリームは、リソース レコードから開きます。 コード文字セットが ascii し、に、ストリームの内容をコピーするかどうかを決定`txtDetails`です。  
  
## <a name="see-also"></a>参照  
 [インターネット発行シナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 3: フィールドのリスト ボックスを表示します。](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)

