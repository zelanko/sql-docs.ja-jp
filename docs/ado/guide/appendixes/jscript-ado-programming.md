---
title: JScript での ADO プログラミング |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da87199347052189e5af8b881154b37723408d1f
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214181"
---
# <a name="jscript-ado-programming"></a>JScript での ADO プログラミング
## <a name="creating-an-ado-project"></a>ADO プロジェクトの作成  
 Microsoft JScript では、プロジェクトの ADO の参照にする必要はありませんので、タイプ ライブラリではサポートしません。 そのため、コマンドラインの入力候補などの関連する機能はサポートされません。 また、既定では、ADO 列挙定数で定義されていない JScript です。  
  
 ただし、ADO では、JScript で使用する次の定義を含むファイルをインクルードする 2 つ提供します。  
  
-   サーバー側のスクリプト使用 Adojavas.inc、ADO ライブラリのフォルダーにインストールされています。  
  
-   クライアント側のスクリプト使用 Adcjavas.inc、ADO ライブラリのフォルダーにインストールされています。  
  
 コピーし、ASP ページにこれらのファイルからの定数の定義を貼り付けるか、サーバー側スクリプトを実行している場合、Web サイト上のフォルダーに Adojavas.inc ファイルをコピーし、次のように、ASP ページから参照します。  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>JScript での ADO オブジェクトの作成  
 代わりに使用する必要があります、 **CreateObject**関数呼び出し。  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>JScript の例  
 次のコードが表示された Active Server Page (ASP) ファイルでの JScript サーバー側プログラミングの汎用例を**Recordset**オブジェクト。  
  
```javascript
<%  @LANGUAGE="JScript" %>  
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
