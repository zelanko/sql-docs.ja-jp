---
title: "キャンセル メソッドの例 (VBScript) |Microsoft ドキュメント"
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
dev_langs:
- VB
helpviewer_keywords:
- Cancel method [ADO], VBScript example
ms.assetid: 4ade106d-063d-486e-bc4d-a1a6b6e0bea9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b403587af4267fa1fd604e7adc57e2a25eded2c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="cancel-method-example-vbscript"></a>キャンセル メソッドの例 (VBScript)
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 次の例を読み取る方法を示しています、[キャンセル](../../../ado/reference/ado-api/cancel-method-ado.md)メソッド実行時にします。 切り取りし、メモ帳などのテキスト エディターに次のコードを貼り付けます CancelVBS.asp として保存します。 結果は、任意のクライアント ブラウザーで表示できます。  
  
```  
<!-- BeginCancelVBS -->  
<Script Language="VBScript">  
<!--  
Sub cmdCancelAsync_OnClick  
   ' Terminates currently running AsyncExecute,  
   ' ReadyState property set to adcReadyStateLoaded,  
   ' Recordset set to Nothing  
  ADC.Cancel  
End Sub  
  
Sub cmdRefreshTable_OnClick  
   ADC.Refresh  
End Sub  
-->  
</Script>  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="ADC">  
.  
   <PARAM NAME="SQL" VALUE="Select FirstName, LastName from Employees">  
   <PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'">  
   <PARAM NAME="Server" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
.  
</OBJECT>  
  
<TABLE DATASRC=#ADC>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
  
<FORM>  
<INPUT type="button" value="Refresh" id=cmdRefreshTable name=cmdRefreshTable>  
<INPUT type="button" value="Cancel" id=cmdCancelAsync name=cmdCancelAsync>  
</FORM>  
<!-- EndCancelVBS -->  
```  
  
## <a name="see-also"></a>参照  
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)


