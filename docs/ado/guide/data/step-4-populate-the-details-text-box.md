---
title: 手順 4:詳細情報のテキスト ボックスに入力 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 060de551afa266dae4d5384fe765e16b997bcccd
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206651"
---
# <a name="step-4-populate-the-details-text-box"></a>手順 4:詳細情報のテキスト ボックスに入力します。
Details テキスト ボックスを設定するには、という名前のサブルーチンを作成**recFields**し、次のコードを挿入します。  
  
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
  
 このコードは、生成`lstDetails`フィールドに渡される単純なレコードの値と`recFields`します。 リソースがテキスト ファイルの場合は、リソース レコードからテキスト Stream が開かれます。 コードでは、文字セットが ascii し、Stream 内容をコピーするかどうかを決定します。`txtDetails`します。  
  
## <a name="see-also"></a>参照  
 [インターネットのシナリオへの発行](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 3:フィールド リスト ボックスを設定します。](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
