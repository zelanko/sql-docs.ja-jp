---
title: '手順 2: Main リスト ボックスの初期化 |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41c340d2d84e80100788ae2d797a37fd048e4264
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735524"
---
# <a name="step-2-initialize-the-main-list-box"></a>手順 2: Main リスト ボックスを初期化する
グローバルのレコードとレコード セット オブジェクトを宣言するには、([全般]) (宣言) Form1 に、次のコードを挿入します。  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 このコードは、このシナリオでは後で使用されるレコードとレコード セット オブジェクトのグローバル オブジェクト参照を宣言します。  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>URL に接続し、lstMain を設定するには  
 Form1 の Form Load イベント ハンドラーに次のコードを挿入します。  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=http://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 このコードは、グローバルのレコードとレコード セット オブジェクトをインスタンス化します。 Record オブジェクトでは、 `grec`、ActiveConnection として指定された URL を開くとします。 URL が存在する場合が開きます。ファイルは既に存在しない場合は作成されます。 置き換える必要がありますに注意してください"http://servername/foldername/"環境からの有効な URL を使用します。  
  
 Recordset オブジェクトを`grs`、レコードの子で開かれた`grec`します。 `lstMain`は URL に公開されているリソースのファイル名が格納されます。  
  
## <a name="see-also"></a>参照  
 [インターネットのシナリオへの発行](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 1: Visual Basic プロジェクトを設定します。](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [手順 3: Fields リスト ボックスに値を設定する](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
