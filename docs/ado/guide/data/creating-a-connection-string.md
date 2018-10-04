---
title: 接続文字列の作成 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41732b25c7b2c02f5b6b8a319e057d204a3a3384
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611393"
---
# <a name="creating-a-connection-string"></a>接続文字列の作成
接続文字列は、セミコロンで区切られた引数と値のペア (つまり、パラメーター) の一覧で構成されます。 以下に例を示します。  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 すべてのパラメーターは、ADO または指定されたプロバイダーで認識する必要があります。  
  
 ADO では、接続文字列に次の 5 つの引数を認識します。  
  
|引数|説明|  
|--------------|-----------------|  
|*Provider*|接続に使用するプロバイダーの名前を指定します。|  
|*[ファイル名]*|事前設定された接続情報を格納しているプロバイダーに固有のファイル (たとえば、永続化されたデータ ソース オブジェクト) の名前を指定します。|  
|*URL*|ファイルやディレクトリなどのリソースを識別する絶対 URL として、接続文字列を指定します。|  
|*リモート プロバイダー*|クライアント側の接続を開くときに使用するプロバイダーの名前を指定します。 (リモート データのサービスのみ。)|  
|*リモート サーバー*|クライアント側の接続を開くときに使用するサーバーのパス名を指定します。 (リモート データのサービスのみ。)|  
  
 という名前のプロバイダーに渡されるその他の引数、*プロバイダー* ADO で処理なしの引数。  
  
 HelloData アプリケーション[HelloData: する単純な ADO アプリケーション](../../../ado/guide/data/hellodata-a-simple-ado-application.md)次の接続文字列を使用します。  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 この接続文字列で ADO が認識するのみ、`"Provider=SQLOLEDB"`パラメーターで、ADO のデータ ソースとして SQL Server 用 Microsoft OLE DB プロバイダーを指定します。 引数と値のペアの残りの部分`"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`、このプロバイダーにもそのまま渡されます。 型とこれらのパラメーターの有効性は、プロバイダー固有です。 接続文字列で渡すことができる有効なパラメーターについては、個々 のプロバイダーのドキュメントを参照してください。  
  
 "Server"を代入する OLE DB Provider for SQL Server のドキュメント、に従って、*データ ソース*パラメーターと「データベース」を*Initial Catalog*パラメーター。 したがって、次の接続文字列では、上記と同じ結果が生成。  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
