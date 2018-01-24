---
title: "XML データへのビジネス ロジックの追加 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0fe9d8795c09148771bf9d1d513b403976c6a3a2
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="add-business-logic-to-xml-data"></a>XML データへのビジネス ロジックの追加
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] XML データにはいくつかの方法でビジネス ロジックを追加できます。  
  
-   XML データの挿入や変更のときに領域固有の制約を強制する行制約または列制約を記述できます。  
  
-   列の値を挿入または更新したときに起動するトリガーを XML 列に記述できます。 トリガーには領域固有の検証規則を含めたり、トリガーを使用してプロパティ テーブルにデータを格納することができます。  
  
-   データベース エンジンには、マネージ コードを実行する機能が含まれています。 この共通言語ランタイム (CLR) 統合を使用すると、XML 値を渡す関数をマネージ コードに記述し、System.Xml 名前空間の提供する XML 処理機能を使用できます。 たとえば、XML データに XSL 変換を適用する場合に使用します。 または、XML のシリアル化を解除して 1 つ以上のマネージ クラスにし、マネージ コードで操作することができます。  
  
-   ビジネス ニーズに合わせて XML 列の処理を開始する Transact-SQL ストアド プロシージャや関数を記述できます。  
  
## <a name="example-applying-xsl-transformation"></a>例 : XSL 変換の適用  
 **xml** データ型のインスタンスおよびファイルに保存されている XSL 変換を受け取り、XML データに変換を適用し、変換後の XML を結果として返す CLR 関数 **TransformXml()** を考えてみます。 次に示すのは、C# で記述した関数の骨組みです。  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 アセンブリを登録し、 [!INCLUDE[tsql](../../includes/tsql-md.md)] TransformXml() **に対応する** のユーザー定義関数 **SqlXslTransform()**を作成すると、次のクエリに示すように Transact-SQL からその関数を呼び出すことができます。  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 クエリの結果には、変換後の XML の行セットが含まれます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に CLR を統合することによって、XML データをテーブルに分解するかプロパティを昇格させてから、System.Xml 名前空間のマネージ クラスを使用して XML データにクエリを実行できるようになります。 詳細については、「[XML データ &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)」を参照してください。  
  
  
