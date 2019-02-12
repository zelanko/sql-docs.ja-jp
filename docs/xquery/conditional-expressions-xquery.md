---
title: 条件式 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 62a061632b5f598932fe29499519d7eb897c78a6
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041743"
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
  
 `expression1` の実効ブール値に応じて、`expression2` または `expression3` が評価されます。 以下に例を示します。  
  
-   テスト式 `expression1` の結果が空のシーケンスになった場合、結果は False になります。  
  
-   テスト式 `expression1` の結果が単純なブール値になった場合、この値は式の結果になります。  
  
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
  
 これは、結果です。  
  
```  
<FirstName>fname</FirstName>  
```  
  
 次のクエリは、特定の製品モデルの製品カタログの説明から、最初の 2 つの製品の特徴の記述を取得します。 ドキュメントに複数の特徴が記述されている場合は、内容のない <`there-is-more`> 要素が追加されます。  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
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
  
 これは、結果です。  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  \<p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p1:WarrantyPeriod>3 years\</p1:WarrantyPeriod>  
    \<p1:Description>parts and labor\</p1:Description>  
  \</p1:Warranty>  
  \<p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p2:NoOfYears>10 years\</p2:NoOfYears>  
    \<p2:Description>maintenance contract available through your dealer or any AdventureWorks retail store.\</p2:Description>  
  \</p2:Maintenance>  
  \<there-is-more />  
</Product>  
```  
  
 次のクエリでは、ワーク センターでセットアップ時間が指定されていない場合に、<`Location`> に LocationID 属性が設定されて、返されます。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
 これは、結果です。  
  
```  
<WorkCenterLocation LocationID="30" />  
<WorkCenterLocation LocationID="45" />  
<WorkCenterLocation LocationID="60" />  
```  
  
 なしこのクエリを記述することができます、**場合**句では、次の例に示すようにします。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
  
