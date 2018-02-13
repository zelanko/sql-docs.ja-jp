---
title: "CommandText プロパティを使用して、テンプレート ファイルの実行 |Microsoft ドキュメント"
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
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- executing template files [SQLXML]
- CommandText property
ms.assetid: f1b1278d-252d-4a06-836e-4ef77f338ef9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef0cc4fe9655e7ac183226f01bfba0a7a3901971
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="executing-template-files-by-using-the-commandtext-property"></a>CommandText プロパティを使用した、テンプレート ファイルの実行
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
この例では、SQL または XPath クエリで構成されるテンプレート ファイルを CommandTextproperty を使用して指定する方法を示しています。 CommandText の値として、SQL または XPath クエリを指定する、代わりに、値として、ファイル名を指定できます。 次の例では、CommandType プロパティが SqlXmlCommandType.TemplateFile として指定されます。  
  
 サンプル アプリケーションでは、次のテンプレートが実行されます。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 これは C# サンプル アプリケーションです。 このアプリケーションをテストするには、テンプレート (TemplateFile.xml) を保存した後、アプリケーションを実行します。  
  
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
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandType = SqlXmlCommandType.TemplateFile;  
         cmd.CommandText = "TemplateFile.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
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
  
1.  コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされていることを確認します。  
  
2.  この例で提供される XML テンプレート (TemplateFile.xml) をフォルダーに保存します。  
  
3.  この例では、スキーマが格納されている同じフォルダーに、c# コード (DocSample.cs が指定されている) を保存します。 ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。  
  
4.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
5.  コマンド プロンプトで、DocSample.exe を実行します。  
  
 パラメーター名がアット マークで始まる必要がありますをテンプレートにパラメーターを渡す場合 (@) です。たとえば、p.Name="@ContactID"SqlXmlParameter オブジェクトである場合、します。  
  
 次は、1 つのパラメーターをとるように変更したテンプレートです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='ContactID'>1</sql:param>    
  </sql:header>  
  <sql:query>  
    SELECT ContactID, FirstName, LastName  
    FROM   Person.Contact  
    WHERE  ContactID=@ContactID  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 次は、テンプレートを実行するパラメーターを渡すように変更したコードです。  
  
```  
public static int testParams()  
{  
  
   Stream strm;  
   SqlXmlParameter p;  
  
   SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
   cmd.CommandType = SqlXmlCommandType.TemplateFile;  
   cmd.CommandText = "TemplateFile.xml";  
   p = cmd.CreateParameter();  
   p.Name="@ContactID";  
   p.Value = "1";  
   strm = cmd.ExecuteStream();  
   StreamReader sw = new StreamReader(strm);  
   Console.WriteLine(sw.ReadToEnd());  
   return 0;        
}  
```  
  
  
