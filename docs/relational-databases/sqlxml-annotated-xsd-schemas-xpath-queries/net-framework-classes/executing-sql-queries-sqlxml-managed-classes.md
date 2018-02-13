---
title: "SQL クエリの実行 (SQLXML マネージ クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 828ccc1035b3fffc0eb1184e47a2af8a389dc29f
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a>SQL クエリの実行 (SQLXML マネージ クラス)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
この例では、次のことを行います。  
  
-   パラメーター (SqlXmlParameter オブジェクト) を作成します。  
  
-   SqlXmlParameter オブジェクトのプロパティ (名前と値) に値を代入します。  
  
 この例では、単純な SQL クエリを実行して、従業員の姓、名、および誕生日を取得します。従業員の姓の値はパラメーターとして渡されます。 パラメーターを指定するときに (*LastName*)、Value プロパティのみを設定します。 Name プロパティが設定されていないため、このクエリでは、パラメーターは位置指定し、名前は必要ありません。  
  
 既定では SqlXmlCommand オブジェクトの CommandType プロパティが**Sql**です。 したがって、このプロパティは明示的に設定しません。  
  
> [!NOTE]  
>  コードでは、接続文字列に Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
 この C# コードは次のとおりです。  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
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
  
1.  このトピックで提供される C# コード (DocSample.cs) をフォルダーに保存します。  
  
2.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
3.  コマンド プロンプトで、DocSample.exe を実行します。  
  
 この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。  
  
 コマンド テキストとして SQL クエリを指定する代わりに、次のコード フラグメントのようなテンプレートを指定して、(同様にテンプレートとして提供されている) アップデートグラムを実行し、顧客レコードを挿入することもできます。 テンプレートとアップデートグラムはファイル内に指定し、ファイルとして実行できます。 詳細については、次を参照してください。 [CommandText プロパティを使用して、テンプレート ファイルを実行する](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-template-files-by-using-the-commandtext-property.md)です。  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a>ExecuteToStream の使用  
 既存のストリームがある場合は、ストリーム オブジェクトを作成して、Execute メソッドを使用してではなく ExecuteToStream メソッドを使用できます。 前の例のコードは ExecuteToStream メソッドを使用してここ改訂します。  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  XmlReader オブジェクトを返す ExecuteXMLReadermethod を使用することもできます。 詳細については、次を参照してください。 [ExecuteXMLReader メソッドを使用して SQL クエリを実行する](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/executing-sql-queries-by-using-the-executexmlreader-method.md)です。  
  
  
