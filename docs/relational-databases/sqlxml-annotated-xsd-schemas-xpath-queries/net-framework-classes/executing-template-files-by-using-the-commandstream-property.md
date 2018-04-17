---
title: CommandStream プロパティを使用して、テンプレート ファイルの実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: be8ac123cdac0096c601aed3874ce4cab045d2e4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a>CommandStream プロパティを使用した、テンプレート ファイルの実行
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  この例では、SqlXmlCommand オブジェクトの CommandStream プロパティを使用して、SQL または XPath クエリで構成されるテンプレート ファイルを指定する方法を示しています。 このアプリケーションでは、コマンド ファイルの場合、FileStreamobject が開かれ、実行される CommandStream としてファイル ストリームが割り当てられます。  
  
 次の例では、CommandType プロパティが (TemplateFile) ではなく SqlXmlCommandType.Template として指定されます。  
  
 次はサンプル XML テンプレートです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 これはサンプル C# アプリケーションです。 このアプリケーションをテストするには、テンプレート (TemplateFile.xml) を保存した後、アプリケーションを実行します。 このアプリケーションでは、XML テンプレートに指定されているクエリが実行され、生成された XML ドキュメントが画面に表示されます。  
  
> [!NOTE]  
>  コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  この例で提供される XML テンプレート (TemplateFile.xml) をフォルダーに保存します。  
  
2.  この例では、スキーマが格納されている同じフォルダーに、c# コード (DocSample.cs が指定されている) を保存します。 ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。  
  
3.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
4.  コマンド プロンプトで、DocSample.exe を実行します。  
  
  
