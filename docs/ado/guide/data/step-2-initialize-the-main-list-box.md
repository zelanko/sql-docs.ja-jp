---
title: "手順 2: メイン リスト ボックスの初期化 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60ece26fab2c6f691614b609d1dd3f07f42231e4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="step-2-initialize-the-main-list-box"></a>手順 2: メイン リスト ボックスを初期化します。
グローバルのレコードと、レコード セット オブジェクトを宣言するには、([全般]) (宣言) Form1 に次のコードを挿入します。  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 このコードでは、このシナリオでは後で使用されるレコードと、レコード セット オブジェクトのグローバル オブジェクト参照を宣言します。  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>URL に接続し、lstMain を設定するには  
 Form1 のフォームの読み込みイベント ハンドラーに次のコードを挿入します。  
  
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
  
 このコードは、グローバルのレコードと、レコード セット オブジェクトをインスタンス化します。 Record オブジェクト`grec`、ActiveConnection として指定された URL でが開きます。 URL が存在する場合は、開かれています。これは既に存在しない場合は作成されます。 お客様の環境から"http://servername/foldername/"の有効な URL を置き換える必要がありますに注意してください。  
  
 レコード セット オブジェクト`grs`、レコードの子で開かれる`grec`です。  `lstMain` URL に公開されているリソースのファイル名が格納されます。  
  
## <a name="see-also"></a>参照  
 [インターネット発行シナリオ](../../../ado/guide/data/internet-publishing-scenario.md)   
 [手順 1: Visual Basic プロジェクトの設定します。](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [手順 3: Fields リスト ボックスに値を設定する](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
