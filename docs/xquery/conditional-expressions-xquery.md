---
title: 条件式 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, conditional expressions
- expressions [XQuery], conditional
- effective Boolean value [XQuery]
- if-then-else statement [XQuery]
- conditional expressions [XQuery]
- EBV
ms.assetid: b280dd96-c80f-4c51-bc06-a88d42174acb
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3634414fb0353c9152d317c718707c3ce26ec812
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979014"
---
# <a name="conditional-expressions-xquery"></a>条件式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery は、次の条件をサポートしている**if then else**ステートメント。  
  
```  
if (<expression1>)  
then  
  <expression2>  
else  
  <expression3>  
```  
  
 有効なブール値に応じて`expression1`, か、`expression2`または`expression3`が評価されます。 以下に例を示します。  
  
-   テスト式 `expression1` の結果が空のシーケンスになった場合、結果は False になります。  
  
-   場合テスト式`expression1`、単純なブール値、この値に結果が式の結果。  
  
-   テスト式 `expression1` の結果が複数ノードのシーケンスになった場合、式の結果は True になります。  
  
-   それ以外の場合は、静的エラーが発生します。  
  
 また、次の点を注意してください。  
  
-   テスト式は、かっこで囲む必要があります。  
  
-   **他**式が必要です。 これが必要ない場合は、このトピックの例にあるように、" ( ) " を返すことができます。  
  
 に対して次のクエリを指定するなど、 **xml**型の変数。 **場合**条件は、SQL 変数の値をテスト (@v) を使用して XQuery 式の内部で、 [sql:variable() 関数](../xquery/xquery-extension-functions-sql-variable.md)拡張関数。 変数の値が "FirstName" の場合、<`FirstName`> 要素が返されます。 それ以外の場合は、<`LastName`> 要素が返されます。  
  
```  
declare @x xml  
declare @v varchar(20)  
set @v='FirstName'  
set @x='  
<ROOT rootID="2">  
  <FirstName>fname</FirstName>  
  <LastName>lname</LastName>  
</ROOT>'  
SELECT @x.query('  
if ( sql:variable("@v")="FirstName" ) then  
  /ROOT/FirstName  
 else  
   /ROOT/LastName  
')  
```  
  
 結果を次に示します。  
  
```  
<FirstName>fname</FirstName>  
```  
  
 次のクエリは、特定の製品モデルの製品カタログの説明から、最初の 2 つの製品の特徴の記述を取得します。 ドキュメントに複数の特徴が記述されている場合は、内容のない <`there-is-more`> 要素が追加されます。  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /p1:ProductDescription/@ProductModelID }  
          { /p1:ProductDescription/@ProductModelName }   
          {  
            for $f in /p1:ProductDescription/p1:Features/*[position()\<=2]  
            return  
            $f   
          }  
          {  
            if (count(/p1:ProductDescription/p1:Features/*) > 2)  
            then \<there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 上記のクエリでは、条件、**場合**式は、複数の 2 つの子要素があるかどうかを確認します。 <`Features`>。 3 つ以上ある場合は、結果に `\<there-is-more/>` 要素が返されます。  
  
 結果を次に示します。  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  \<p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p1:WarrantyPeriod>3 years\</p1:WarrantyPeriod>  
    \<p1:Description>parts and labor\</p1:Description>  
  \</p1:Warranty>  
  \<p2:Maintenance xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p2:NoOfYears>10 years\</p2:NoOfYears>  
    \<p2:Description>maintenance contract available through your dealer or any AdventureWorks retail store.\</p2:Description>  
  \</p2:Maintenance>  
  \<there-is-more />  
</Product>  
```  
  
 次のクエリで、<`Location`>、ワーク センター拠点でセットアップ時間が指定されていない場合、LocationID 属性を持つ要素が返されます。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        for $WC in //AWMI:root/AWMI:Location  
        return  
        if ( $WC[not(@SetupHours)] )  
        then  
          <WorkCenterLocation>  
             { $WC/@LocationID }   
          </WorkCenterLocation>  
         else  
           ()  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 結果を次に示します。  
  
```  
<WorkCenterLocation LocationID="30" />  
<WorkCenterLocation LocationID="45" />  
<WorkCenterLocation LocationID="60" />  
```  
  
 なしこのクエリを記述することができます、**場合**句では、次の例に示すようにします。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in //AWMI:root/AWMI:Location[not(@SetupHours)]   
        return  
          <Location>  
             { $WC/@LocationID }   
          </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
## <a name="see-also"></a>参照  
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
