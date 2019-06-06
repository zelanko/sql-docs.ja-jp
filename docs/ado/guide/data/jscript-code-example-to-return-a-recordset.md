---
title: レコード セットを返す JScript コードの例 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- Recordset [ADO]
ms.assetid: 74aad8a6-06cc-4a2c-811a-d78f9b741d84
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbb484ea6e505940097ff223edb5439944305413
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701975"
---
# <a name="jscript-code-example-to-return-a-recordset"></a>レコードセットを返す JScript コードの例
## <a name="jscript-code-rsjs"></a>JScript コード (rs.js)  
  
```  
main();  
  
function main()  
{  
  DP = "SQLOLEDB";  
  DS = "MySQLServer";  
  DB = "NORTHWIND";  
  
  adOpenForwardOnly = 0;  
  adLockReadOnly = 1;  
  adCmdText = 1;  
  try   
  {  
    var objRs = new ActiveXObject("ADODB.Recordset");  
  }  
  catch (e)  
  {  
    alert("ADODB namespace not found.");  
    exit(0);  
  }  
  
  strConn =  "Provider="         +DP+  
            ";Initial Catalog="  +DB+  
            ";Data Source="      +DS+  
            ";Integrated Security=SSPI;"  
  strComm = "SELECT ProductID,ProductName,UnitPrice "+  
            "FROM Products " +   
            "WHERE CategoryID = 7"  // select Produce  
  
  objRs.open(strComm,   
             strConn,   
             adOpenForwardOnly,  
             adLockReadOnly,  
             adCmdText);  
  
  objRs.MoveFirst();  
  while (objRs.EOF != true)   
  {  
    alert(objRs("ProductID")+"\t"  
         +objRs("ProductName")+"\t"  
         +objRs("UnitPrice"));  
    objRs.MoveNext();  
  }  
  
  objRs.Close  
  objRs = null;  
}  
  
function alert(str)  
{  
  WScript.Echo(str);  
}  
```  
  
#### <a name="try-it"></a>これをお試しください。  
  
1.  上記のコードをテキスト ファイルに保存します。 Rs.js として保存します。  
  
2.  コマンド プロンプトを開き、JScript ファイル (rs.js) を保存したディレクトリに移動します。  
  
3.  型`CScript rs.js`コマンド プロンプトからです。
