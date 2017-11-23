---
title: "VBScript ADO プログラミング |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bc6c05e67582f623b73d9f19882feba36032913f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="vbscript-ado-programming"></a>VBScript ADO プログラミング
## <a name="creating-an-ado-project"></a>ADO プロジェクトを作成します。  
 Microsoft Visual Basic、Scripting Edition はサポートしないタイプ ライブラリのため、プロジェクト内で ADO を参照する必要はありません。 そのため、コマンドラインの入力候補などの関連する機能はサポートされません。 また、既定では、ADO 列挙定数で定義されていない VBScript です。  
  
 ただし、ADO は VBScript で使用する次の定義を含むファイルをインクルードする、2 つを用意しています。  
  
-   サーバー側スクリプトの用途に Adovbs.inc がインストールされている、c:\Program files \common files Files\System\ado\ フォルダーに既定でします。  
  
-   クライアント側スクリプトの用途に Adcvbs.inc がインストールされている、c:\Program files \common files Files\System\msdac\ フォルダーに既定でします。  
  
 コピーし、ASP ページにこれらのファイルからの定数の定義を貼り付けるか、サーバー側スクリプトを実行する場合、Web サイト上のフォルダーに Adovbs.inc ファイルをコピーし、次のように、ASP ページから参照します。  
  
```  
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>VBScript で ADO オブジェクトの作成  
 使用することはできません、 **Dim** VBScript で特定の型にオブジェクトを代入するステートメント。 また、VBScript はサポートしません、**新規**で使用される構文、 **Dim**アプリケーション用の Visual Basic でのステートメント。 代わりに使用する必要があります、 **CreateObject**関数呼び出し。  
  
```  
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>VBScript の例  
 次のコードでは、Active Server Page (ASP) ファイルで VBScript サーバー側のプログラミングの汎用例を示します。  
  
```  
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 特定の VBScript の例では、ADO のドキュメントに含まれて。 詳細については、次を参照してください。 [ADO のコード例では、Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md)です。  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>VBScript および Visual Basic の違い  
 VBScript で ADO を使用することは、Visual basic 構文の使用方法など、さまざまな方法で ADO を使用してに似ています。 ただし、いくつかの重要な違いがあります。  
  
-   VBScript では、のみ、Variant データ型の異なる種類のデータを保持できるをサポートします。 Variant データ型に必要なデータを格納でき、キャスト VBScript によって実行されるため、データは適切に機能します。 ADO で必要な型を認識し、それに応じて、バリアント型の値に変換します。  
  
-   使用することはできません**エラー goto で\<ラベル >** VBScript 内です。  
  
-   VBScript をサポートしているいくつかの組み込みの Visual Basic 関数など**Msgbox**、**日付**、および**IsNumeric**です。 ただし、VBScript は、Visual Basic のサブセットであるために、すべての組み込み関数はサポートされます。 たとえば、VBScript はサポートされません、**形式**関数およびファイル I/O 関数。
