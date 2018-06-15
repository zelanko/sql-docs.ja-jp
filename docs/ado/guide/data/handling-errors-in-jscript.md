---
title: JScript でのエラー処理 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- errors [ADO], JScript
- JScript error handling [ADO]
ms.assetid: 3de527e5-2e65-4ab0-9b7f-6d317c4478de
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcebaef8a36961a5c28af4eee80fca4d088b9ed5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270871"
---
# <a name="handling-errors-in-jscript"></a>JScript でのエラーを処理
Microsoft® JScript® コードを確認する必要があります、**カウント**のプロパティ、**接続**オブジェクトの**エラー**コレクション。 値が 0 より大きい場合は、コレクションを反復処理し、他の言語のいずれかのように値を印刷します。  
  
```  
<!-- BeginErrorExampleJS -->  
<%@ Language=JScript %>  
<HTML>  
<HEAD>  
<title>Error Handling Example (JScript)</title>  
</HEAD>  
<BODY>  
<h1>Error Handling Example (JScript)</h1>  
<%  
   var cnn1 = Server.CreateObject("ADODB.Connection");  
   var errLoop = Server.CreateObject("ADODB.Error");  
   var strError = new String;  
  
   // Intentionally trigger an error.  
   cnn1.Open("nothing");  
  
   if (cnn1.Errors.Count > 0) {  
      // Enumerate Errors collection and display  
      // properties of each Error object.  
      for (var i = 1; i < cnn1.Errors.Count; i++) {  
         errLoop = cnn1.Errors(i);  
         strError = "Error #" & errLoop.Number + "<br>" +  
            "   " + errLoop.Description + "<br>" +  
            "   (Source: " & errLoop.Source & ")" + "<br>" +  
            "   (SQL State: " & errLoop.SQLState + ")" + "<br>" +  
            "   (NativeError: " & errLoop.NativeError + ")" + "<br>";  
         if (errLoop.HelpFile == "")  
            strError = strError +  
               "   No Help file available" +  
               "<br><br>";  
         else  
            strError = strError +  
               "   (HelpFile: " & errLoop.HelpFile & ")" & "<br>" +  
               "   (HelpContext: " & errLoop.HelpContext & ")" +  
               "<br><br>";  
         Response.Write("<p>" & strError & "</p>");  
      }  
   }  
%>  
  
</BODY>  
</HTML>  
<!-- EndErrorExampleJS -->  
```
