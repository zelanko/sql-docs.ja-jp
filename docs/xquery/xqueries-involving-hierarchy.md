---
title: 階層に関連する XQueries |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- hierarchies [XQuery]
- XQuery, hierarchies
ms.assetid: 6953d8b7-bad8-4b64-bf7b-12fa4f10f65c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3296807e7470c84a4df2f3960ea01185c5915048
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597061"
---
# <a name="xqueries-involving-hierarchy"></a>階層に関係する XQuery
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ほとんど**xml**内の列を入力、 **AdventureWorks**データベースは半構造化ドキュメント。 したがって、各行に格納されたドキュメントは異なって見える場合があります。 このトピックのクエリ サンプルでは、このようなさまざまなドキュメントから情報を抽出する方法について示します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-from-the-manufacturing-instructions-documents-retrieve-work-center-locations-together-with-the-first-manufacturing-step-at-those-locations"></a>A. 製造命令ドキュメントから、ワーク センターの場所とその場所の最初の製造手順を取得  
 クエリに XML を構築、製品モデル 7 の <`ManuInstr`> 要素で**ProductModelID**と**ProductModelName**属性、および 1 つまたは複数 <`Location`>子要素。  
  
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
  
-   **Sql:column()** 構築される XML にリレーショナル値を含めるために使用します。  
  
-   <`Location`> 要素を構築する際に、$wc/@* でそのワーク センターの場所のすべての属性が取得されます。  
  
-   **String()** 関数から文字列値を返します、<`step`> 要素。  
  
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
 次のクエリは、階層全体を検索して特定の顧客の連絡先の追加の電話番号を取得します <`telephoneNumber`> 要素。 <`telephoneNumber`> 要素はどこにでも表示、階層では、クエリで子孫や自己演算子を使用 (//) で検索します。  
  
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
  
 具体的には、最上位レベルの電話番号のみを取得する、<`telephoneNumber`> の子要素 <`AdditionalContactInfo`>、クエリの FOR 式を変更するには  
  
 `for $ph in /ci:AdditionalContactInfo/act:telephoneNumber`。  
  
## <a name="see-also"></a>関連項目  
 [XQuery の基礎](../xquery/xquery-basics.md)   
 [XML の構築&#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)  
  
  
