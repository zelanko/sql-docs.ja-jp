---
title: 示しますメソッドを使用して SQL クエリを実行します。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7387f257e7fb19ca3ec79aaf1bfc2d2f3f799584
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113722"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a>ExecuteXMLReader メソッドを使用した、SQL クエリの実行
  ExecuteToStream メソッドを使用するのではなく、示しますオブジェクトのメソッド、SqlXmlCommand コマンドを実行するために使用できます。 このメソッドは、さらに、結果は (この例では、要素名または属性名と値を印刷) の処理のために使用できる XmlReader オブジェクトを返します。  
  
> [!NOTE]  
>  コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされていることを確認します。  
  
2.  フォルダー内には、このトピックの C# コード (DocSample.cs) が用意されていることを保存します。  
  
3.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
4.  コマンド プロンプトで、DocSample.exe を実行します。  
  
  
