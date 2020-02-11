---
title: '手順 2: メインリストボックスを初期化する |Microsoft Docs'
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
ms.openlocfilehash: 8ad89d806f8a6774cb0fe2de056e30fd274a517c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924083"
---
# <a name="step-2-initialize-the-main-list-box"></a>手順 2: Main リスト ボックスを初期化する
グローバルレコードとレコードセットオブジェクトを宣言するには、Form1 の (宣言) に次のコードを挿入します。  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 このコードは、このシナリオで後ほど使用するレコードおよびレコードセットオブジェクトのグローバルオブジェクト参照を宣言します。  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>URL に接続して lstMain を設定するには  
 Form1 のフォーム読み込みイベントハンドラーに次のコードを挿入します。  
  
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
  
 このコードは、グローバルレコードとレコードセットオブジェクトをインスタンス化します。 レコードオブジェクト`grec`は、ActiveConnection として指定された URL で開かれます。 URL が存在する場合は、それが開かれます。まだ存在しない場合は、作成されます。 "<https://servername/foldername/>" は、使用している環境の有効な URL に置き換える必要があることに注意してください。  
  
 レコードセットオブジェクト`grs`は、レコードの子で開かれ`grec`ます。 次`lstMain`に、URL に発行されたリソースのファイル名を入力します。  
  
## <a name="see-also"></a>参照  
 [インターネット公開のシナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 1: Visual Basic プロジェクトを設定する](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [手順 3: Fields リスト ボックスに値を設定する](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
