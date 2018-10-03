---
title: '手順 5: DataControl が使用可能に (RDS チュートリアル) |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f25c8276c6985e38f0beef46c8db7d60f6e16a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734510"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>手順 5: DataControl が使用可能になる (RDS チュートリアル)
返された**レコード セット**オブジェクトは、使用するために使用します。 確認、移動、またはその他のように編集**Recordset**します。 行うことができます、 **Recordset**環境によって異なります。 Visual Basic および Visual C を使用できるビジュアル コントロールがある、**レコード セット**直接的または間接的に有効にすると、データ コントロールの aid を使用します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
 たとえば、Microsoft Internet Explorer で Web ページを表示する場合があります表示する、 **Recordset** visual コントロール内のデータをオブジェクトします。 Web ページ上のビジュアルのコントロールにアクセスできません、 **Recordset**オブジェクトに直接します。 ただし、アクセスできる、 **Recordset**オブジェクト、 [rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)します。 **Rds.DataControl**ビジュアルで使用可能になりますが制御その[SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)プロパティに設定されて、 **Recordset**オブジェクト。  
  
 コントロールのビジュアル オブジェクトにはその**DATASRC**パラメーターに設定、 **rds.DataControl**、およびその**DATAFLD**プロパティに設定、**レコード セット**オブジェクト フィールド (列)。  
  
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
