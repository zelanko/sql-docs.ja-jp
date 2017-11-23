---
title: "コマンド ストリーム |Microsoft ドキュメント"
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
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46ef9db34ecfc7ee0ba3fbd41a052658a065a010
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="command-streams"></a>コマンド ストリーム
ADO で指定された文字列の形式でコマンドの入力を常にサポートされている、 **CommandText**プロパティです。 代わりに、ADO 2.7 以降を使用することも、情報のストリーム コマンドの入力のストリームを割り当てることによって、 **CommandStream**プロパティです。 ADO を割り当てることができます**ストリーム**オブジェクト、または COM をサポートする任意のオブジェクト**IStream**インターフェイスです。  
  
 コマンド ストリームのコンテンツ渡されるだけです ADO から、プロバイダーに、プロバイダーがこの機能を使用するためのストリームによって入力されたコマンドをサポートするようにします。 たとえば、SQL Server では、XML テンプレートや OpenXML Transact SQL 拡張機能の形式でクエリをサポートしています。  
  
 ストリームの詳細については、プロバイダーで解釈する必要があります、ために設定でコマンド言語を指定する必要があります、 **Dialect**プロパティです。 値**Dialect**プロバイダーによって定義されている GUID を含む文字列です。 有効な値について**Dialect**プロバイダーによってサポートされている、プロバイダーのドキュメントを参照してください。  
  
## <a name="xml-template-query-example"></a>XML テンプレートのクエリ例  
 次の例は、VBScript で Northwind データベースに書き込まれます。  
  
 最初に、初期化して開く、**ストリーム**クエリ ストリームを格納するために使用するオブジェクト。  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 クエリのストリームの内容を XML テンプレート クエリとなります。  
  
 テンプレートのクエリには、sql によって識別される XML 名前空間への参照が必要です。 プレフィックス、 \<sql:query > タグです。 SQL SELECT ステートメントは、XML テンプレートのコンテンツとして含まれており、次のように文字列変数に割り当てられています。  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 次に、文字列をストリームに書き込みます。  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 AdoStreamQuery を割り当てる、 **CommandStream** ADO の**コマンド**オブジェクト。  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 コマンド言語を指定する**Dialect**、SQL Server OLE DB プロバイダーがコマンド ストリームを解釈する方法を示します。 プロバイダー固有の GUID で指定された言語:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 最後に、クエリを実行し、結果を返す、 **Recordset**オブジェクト。  
  
```  
Set objRS = adoCmd.Execute  
```
