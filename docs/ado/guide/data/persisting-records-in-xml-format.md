---
title: "XML 形式で保持するレコード |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- XML persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: f3113ec4-ae31-428f-89c6-bc1024f128ea
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a45c434bdcf551e97eb97f85997ab73c883b599c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="persisting-records-in-xml-format"></a>XML 形式で保持するレコード
Adtg 形式形式のように**Recordset**永続性 XML 形式では、Microsoft OLE DB 永続化プロバイダーが実装されています。 このプロバイダーは、保存されている XML ファイルまたは ADO によって生成されるスキーマ情報を格納しているストリームから順方向専用、読み取り専用の行セットを生成します。 同様に、ADO をかかる**レコード セット**、XML を生成し、ファイルまたは COM を実装する任意のオブジェクトに保存、 **IStream**インターフェイスです。 (ファイルをサポートするオブジェクトの一例は、実際には、 **IStream**)。バージョン 2.5 以降では、ADO 依存している場合に、Microsoft XML パーサー (MSXML) に XML を読み込む、**レコード セット**; したがって行いますが必要です。  
  
> [!NOTE]
>  階層を保存するときにいくつかの制限が適用**レコード セット**(データ図形) を XML 形式にします。 場合、XML に保存することはできません、階層**レコード セット**保留中の更新を含むパラメーター化されたを保存することはできませんと階層**レコード セット**です。 詳細については、次を参照してください。[永続化するフィルター処理され、階層レコード セット](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)です。  
  
 最も簡単な方法を XML にデータを保持し、再び読み込む再度 ADO では、**保存**と**開く**メソッド、それぞれします。 内のデータを保存する次の ADO コード例を**タイトル**titles.sav というファイルにテーブルです。  
  
```  
Dim rs as new Recordset  
Dim rs2 as new Recordset  
Dim c as new Connection  
Dim s as new Stream  
  
' Query the Titles table.  
c.Open "provider=sqloledb;data source=MySQLServer;initial catalog=pubs;Integrated Security='SSPI'"  
rs.cursorlocation = adUseClient  
rs.Open "select * from titles", c, adOpenStatic  
  
' Save to the file in the XML format. Note that if you don't specify   
' adPersistXML, a binary format (ADTG) will be used by default.  
rs.Save "titles.sav", adPersistXML  
  
' Save the recordset into the ADO Stream object.  
rs.save s, adPersistXML  
rs.Close  
c.Close  
  
set rs = nothing  
  
' Reopen the file.  
rs.Open "titles.sav",,,,adCmdFile  
' Open the Stream back into a Recordset.  
rs2.open s  
```  
  
 ADO には常に、全体が引き続き発生する**Recordset**オブジェクト。 行のサブセットを保持するかどうか、 **Recordset**オブジェクトを使用して、**フィルター**行を絞り込むか、選択句を変更する方法です。 ただし、開く必要があります、 **Recordset**クライアント側カーソルを持つオブジェクト (**CursorLocation** = **adUseClient**) を使用する、 **をフィルター処理**行のサブセットを保存するためのメソッドです。 たとえば、文字"b"で始まるタイトルを取得することができますフィルターを適用する開いた**Recordset**オブジェクト。  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO では、スクロール可能な生成するために、クライアント カーソル エンジン行セットが使用して常にブックマークを設定**Recordset**永続化プロバイダーによって生成された順方向専用のデータの上にオブジェクト。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [XML の永続化の形式](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [名前空間](../../../ado/guide/data/namespaces.md)  
  
-   [スキーマ セクション](../../../ado/guide/data/schema-section.md)  
  
-   [データ セクション](../../../ado/guide/data/data-section.md)  
  
-   [XML での階層のレコード セット](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [XML 内のレコード セットの動的プロパティ](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [XSLT 変換](../../../ado/guide/data/xslt-transformations.md)  
  
-   [XML DOM オブジェクトへの保存](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [XML のセキュリティに関する考慮事項](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [XML レコード セットを保存するシナリオ](../../../ado/guide/data/xml-recordset-persistence-scenario.md)

