---
title: 手順 2:メイン リスト ボックスの初期化 |Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 0df631ccaa9cd3a6177cb4e4e8e63c65286ad361
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700364"
---
# <a name="step-2-initialize-the-main-list-box"></a>手順 2:Main リスト ボックスを初期化する
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
    grec.Open "", "URL=https://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 このコードは、グローバルのレコードとレコード セット オブジェクトをインスタンス化します。 Record オブジェクトでは、 `grec`、ActiveConnection として指定された URL を開くとします。 URL が存在する場合が開きます。ファイルは既に存在しない場合は作成されます。 置き換える必要がありますに注意してください"<https://servername/foldername/>"環境からの有効な URL を使用します。  
  
 Recordset オブジェクトを`grs`、レコードの子で開かれた`grec`します。 `lstMain`は URL に公開されているリソースのファイル名が格納されます。  
  
## <a name="see-also"></a>参照  
 [インターネットのシナリオへの発行](../../../ado/guide/data/internet-publishing-scenario.md)   
 [ステップ 1: Visual Basic プロジェクトを設定します。](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [ステップ 3:フィールド リスト ボックスを設定します。](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
