---
title: レコード セットの永続化の詳細 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11bceb2bdeeced8ddbe98e7ddc1164e216644264
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="more-about-recordset-persistence"></a>レコード セットの保存に関する詳細情報
ADO レコード セット オブジェクトのサポートの内容を格納する、**レコード セット**を使用してファイル内のオブジェクトの[保存](../../../ado/reference/ado-api/save-method.md)メソッドです。 永続的に格納されているファイルがローカルに存在がドライブ、サーバー、または Web 上の URL としてサイトです。 ファイルを復元して、いずれかで、後で、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)のメソッド、 **Recordset**オブジェクトまたは[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)のメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
 さらに、 [GetString](../../../ado/reference/ado-api/getstring-method-ado.md)メソッドに変換、 **Recordset**を行と列が指定された文字で区切られたはフォームにオブジェクト。  
  
 永続化する、 **Recordset**ファイルに格納できる形式に変換することから始めます。 **レコード セット**専用 adtg 高度なデータ TableGram (形式) 形式またはオープン拡張マークアップ言語 (XML) 形式でオブジェクトを格納することができます。 Adtg 形式の例は、次のセクションに表示されます。 XML の永続化の詳細については、次を参照してください。 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)です。  
  
 永続化されたファイルには、保留中の変更を保存します。 返すクエリを発行するこれを行うことができます、**レコード セット**オブジェクト、編集、**レコード セット**、し、保留中の変更を保存、復元後、 **Recordset**、し、保存されていると、データ ソースが更新保留中の変更。  
  
 永続的に保存する方法について**ストリーム**、オブジェクトを参照してください[ストリームと永続性](../../../ado/guide/data/streams-and-persistence.md)です。  
  
 例については**Recordset**永続化、XML レコード セットの永続化のシナリオを参照してください。  
  
## <a name="example"></a>例  
  
### <a name="save-a-recordset"></a>レコード セットを保存します。  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Recordset.Open に保存されているファイルを開きます。  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 必要に応じて場合、**レコード セット**はすべての既定値をそのまま使用して、次のコードをアクティブな接続必要はありません。  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Connection.Execute に保存されているファイルを開きます。  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Rds. で永続化されたファイルを開くDataControl:  
 ここで、**サーバー**プロパティが設定されていません。  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>参照  
 [GetString メソッド (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Microsoft OLE DB 永続化プロバイダー (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [ストリームと永続性](../../../ado/guide/data/streams-and-persistence.md)
