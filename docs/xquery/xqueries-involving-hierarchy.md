---
title: "階層に関連する XQueries |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- hierarchies [XQuery]
- XQuery, hierarchies
ms.assetid: 6953d8b7-bad8-4b64-bf7b-12fa4f10f65c
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e1de0946e0e2b65bb3e1e957653c419a1a8a3c2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="xqueries-involving-hierarchy"></a>階層に関係する XQuery
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ほとんど**xml**内の列を入力、 **AdventureWorks**データベースは、半構造化ドキュメント。 したがって、各行に格納されたドキュメントは異なって見える場合があります。 このトピックのクエリ サンプルでは、このようなさまざまなドキュメントから情報を抽出する方法について示します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-from-the-manufacturing-instructions-documents-retrieve-work-center-locations-together-with-the-first-manufacturing-step-at-those-locations"></a>A. 製造命令ドキュメントから、ワーク センターの場所とその場所の最初の製造手順を取得  
 製品モデル 7 の場合、クエリを含む XML を構築、<`ManuInstr`> 要素と**ProductModelID**と**ProductModelName**属性、および 1 つまたは複数 <`Location`>子要素です。  
  
 各 <`Location`> 要素には、一連の独自の属性と 1 つの <`step`> 子要素があります。 これは、<`step`> 子要素は、ワーク センター拠点で最初の製造手順です。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   \<ManuInstr  ProdModelID = "{sql:column("Production.ProductModel.ProductModelID") }"   
                ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
            {   
              for $wc in //AWMI:root/AWMI:Location  
              return  
                <Location>  
                 {$wc/@* }  
                 <step1> { string( ($wc//AWMI:step)[1] ) } </step1>  
                </Location>  
            }  
          </ManuInstr>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **名前空間**キーワード、 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)名前空間プレフィックスを定義します。 このプレフィックスは、後からクエリ本文で使用されます。  
  
-   XML 構築からクエリ評価にクエリを切り替えるために、コンテキスト切り替えトークンの {) と (} が使用されます。  
  
-   **Sql:column()**構築される XML にリレーショナル値を含めるために使用します。  
  
-   <`Location`> 要素を構築する際に、$wc/@* でそのワーク センターの場所のすべての属性が取得されます。  
  
-   **String()**関数から文字列値を返します、<`step`> 要素。  
  
 これは、結果の一部です。  
  
```  
<ManuInstr ProdModelID="7" ProductModelName="HL Touring Frame">  
   <Location LocationID="10" SetupHours="0.5"   
            MachineHours="3" LaborHours="2.5" LotSize="100">  
     <step1>Insert aluminum sheet MS-2341 into the T-85A   
             framing tool.</step1>  
   </Location>  
   <Location LocationID="20" SetupHours="0.15"   
            MachineHours="2" LaborHours="1.75" LotSize="1">  
      <step1>Assemble all frame components following   
             blueprint 1299.</step1>  
   </Location>  
...  
</ManuInstr>   
```  
  
### <a name="b-find-all-telephone-numbers-in-the-additionalcontactinfo-column"></a>B. AdditionalContactInfo 列のすべての電話番号の検索  
 次のクエリは、階層全体を検索することにより、特定の顧客の連絡先の追加の電話番号を取得、<`telephoneNumber`> 要素。 <`telephoneNumber`> 要素どこでも表示できます、階層内のクエリでは子孫や自己演算子 (//) で検索します。  
  
```  
SELECT AdditionalContactInfo.query('  
 declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
 declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
for $ph in /ci:AdditionalContactInfo//act:telephoneNumber  
   return  
      $ph/act:number  
') as x  
FROM  Person.Contact  
WHERE ContactID = 1  
```  
  
 結果を次に示します。  
  
```  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  112-111-1111  
\</act:number>  
```  
  
 具体的には、上位レベルの電話番号のみを取得する、<`telephoneNumber`> の子要素 <`AdditionalContactInfo`>、クエリの FOR 式を変更するには  
  
 `for $ph in /ci:AdditionalContactInfo/act:telephoneNumber`」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [XQuery の基礎](../xquery/xquery-basics.md)   
 [XML の構築と #40 です。XQuery と #41 です。](../xquery/xml-construction-xquery.md)   
 [XML Data &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
