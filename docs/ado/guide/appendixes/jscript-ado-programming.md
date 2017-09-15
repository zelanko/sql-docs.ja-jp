---
title: "JScript ADO プログラミング |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6ae8137c2e5641594c3ddcf768c47b7fe844fafc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="jscript-ado-programming"></a>JScript ADO プログラミング
## <a name="creating-an-ado-project"></a>ADO プロジェクトを作成します。  
 Microsoft JScript は、タイプ ライブラリにはサポートしないため、プロジェクトで ADO 参照にする必要はありません。 そのため、コマンドラインの入力候補などの関連する機能はサポートされません。 また、既定では、ADO 列挙定数で定義されていない JScript です。  
  
 ただし、ADO は JScript と共に使用する次の定義を含むファイルをインクルードする、2 つを用意しています。  
  
-   サーバー側スクリプト使用 Adojavas.inc、ADO ライブラリ フォルダーにインストールされています。  
  
-   クライアント側スクリプト使用 Adcjavas.inc、ADO ライブラリ フォルダーにインストールされています。  
  
 コピーし、ASP ページにこれらのファイルからの定数の定義を貼り付けるか、サーバー側スクリプトを実行する場合、Web サイト上のフォルダーに Adojavas.inc ファイルをコピーし、次のように、ASP ページから参照します。  
  
```  
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>JScript では ADO オブジェクトの作成  
 代わりに使用する必要があります、 **CreateObject**関数呼び出し。  
  
```  
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>JScript の例  
 次のコードが表示されたアクティブ サーバー ページ (ASP) ファイルでの JScript サーバー側プログラミングの汎用例を示します、 **Recordset**オブジェクト。  
  
```  
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
