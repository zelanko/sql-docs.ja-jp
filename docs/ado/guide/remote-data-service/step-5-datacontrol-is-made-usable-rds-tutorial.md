---
title: "手順 5: DataControl が行われた使用可能な (RDS チュートリアル) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f59e167dfad5ddd4b99d784b34e37556a076a2f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>手順 5: DataControl が行われた使用可能な (RDS チュートリアル)
返された**Recordset**オブジェクトは、使用するために使用します。 確認、移動、またはと、他のように編集**Recordset**です。 行うことができます、 **Recordset**環境によって異なります。 Visual Basic および Visual C を使用できるビジュアル コントロールがある、 **Recordset**直接的または間接的に有効にすると、データ コントロールを使用しています。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 たとえば、Microsoft Internet Explorer で Web ページを表示する場合があります表示する、 **Recordset** visual コントロール内のデータをオブジェクトします。 Web ページ上のビジュアル コントロールがアクセスできない、**レコード セット**オブジェクトに直接できます。 ただしにアクセスする、 **Recordset**オブジェクトを介して、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)です。 **.Rds ですDataControl**ビジュアルで使用可能になりますタイミングを制御、 [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)プロパティに設定されている、 **Recordset**オブジェクト。  
  
 ビジュアル コントロール オブジェクトにはその**DATASRC**パラメーターを設定、 **.rds ですDataControl**、およびその**DATAFLD**プロパティに設定、 **Recordset**オブジェクト フィールド (列)。  
  
 このチュートリアルでは、設定、 **SourceRecordset**プロパティ。  
  
```  
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>参照  
 [手順 6: 変更は、サーバー (RDS チュートリアル) に送信されます。](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

