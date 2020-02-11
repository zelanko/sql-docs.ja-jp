---
title: '手順 3: フィールドリストボックスにデータを設定する |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d7f351b90030e755dde8ad13905ef4533eff08e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924058"
---
# <a name="step-3-populate-the-fields-list-box"></a>手順 3: Fields リスト ボックスに値を設定する
[フィールド] ボックスを設定するには、の`lstMain`click イベントハンドラーに次のコードを挿入します。  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 このコードは、ローカルレコードとレコードセットオブジェクト、 `rec`および`rs`をそれぞれ宣言してインスタンス化します。  
  
 で`lstMain`選択されたリソースに対応する行がの現在の`grs`行になります。 次に、[詳細] リストボックス`rec`がクリアされ、ソースと`grs`しての現在の行で開かれます。  
  
 [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)で指定されているように、リソースがコレクションレコードの場合`rs` 、ローカルのレコードセットが rec の子で開かれます。次`lstDetails`に、の`rs`行の値がに格納されます。  
  
 リソースが単純なレコードの場合は`recFields` 、が呼び出されます。 の詳細につい`recFields`ては、次の手順を参照してください。  
  
 リソースが構造化ドキュメントである場合、コードは実装されません。  
  
## <a name="see-also"></a>参照  
 [インターネット公開のシナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 2: メインリストボックスを初期化する](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [手順 4: Details テキスト ボックスに値を設定する](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
