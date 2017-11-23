---
title: "比較式 (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: XML
helpviewer_keywords:
- node comparison operators [XQuery]
- comparison expressions [XQuery]
- node order comparison operators [XQuery]
- expressions [XQuery], comparison
- comparison operators [XQuery]
- value comparison operators
ms.assetid: dc671348-306f-48ef-9e6e-81fc3c7260a6
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 98cb462f370a2008b82983973ecacf1b9a581404
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="comparison-expressions-xquery"></a>比較式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery には、次の種類の比較演算子が用意されています。  
  
-   一般的な比較演算子  
  
-   値の比較演算子  
  
-   ノードの比較演算子  
  
-   ノード順の比較演算子  
  
## <a name="general-comparison-operators"></a>一般的な比較演算子  
 一般的な比較演算子を使用して、アトミック値、シーケンス、またはその 2 つの組み合わせを比較できます。  
  
 一般的な演算子を次の表に定義します。  
  
|演算子|Description|  
|--------------|-----------------|  
|=|等号|  
|!=|等しくないです。|  
|\<|より小さい|  
|>|より大きい|  
|\<=|以下|  
|>=|以上|  
  
 一般的な比較演算子を使用して 2 つのシーケンスを比較するときに、最初のシーケンス内の値との比較結果が True になる値が 2 番目のシーケンス内に存在すると、全体的な比較結果は True になります。 それ以外の場合は False になります。 たとえば、(1, 2, 3) = (3, 4) は両方のシーケンスに値 3 があるので True になります。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3) = (3,4)')    
```  
  
 比較する 2 つの値の型は、比較できる型である必要があります。 具体的には、値の型は静的に確認されます。 数値の比較の場合、数値型の上位変換が発生する場合があります。 たとえば、10 進値の 10 が double 値 1e1 と比較される場合、10 進値が double 値に変換されます。 double 値の比較は正確には行えないので、不正確な結果になる場合があります。  
  
 一方の値が型指定されていない場合は、型指定されていない値が他方の値の型にキャストされます。 次の例では、値 7 が整数として扱われます。 比較する前に、型指定されていない値 /a[1] が整数に変換されます。 整数の比較は True を返します。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < 7')  
```  
  
 型指定されていない値が文字列または他の型指定されていない値と比較される場合は、xs:string にキャストされます。 次のクエリでは、文字列 6 が文字列 "17" と比較されます。 このクエリは文字列の比較になるので、False が返されます。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < "17"')  
```  
  
 次のクエリは、AdventureWorks サンプル データベースで提供されている製品カタログから製品モデルの小さいサイズの写真を返します。 クエリによって返されるアトミック値のシーケンスを比較する`PD:ProductDescription/PD:Picture/PD:Size`単一のシーケンス"small"とします。 比較が True のかどうか、それを返します、< 画像\>要素。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('         
    for $P in /PD:ProductDescription/PD:Picture[PD:Size = "small"]         
    return $P') as Result         
FROM   Production.ProductModel         
WHERE  ProductModelID=19         
```  
  
 次のクエリで電話番号のシーケンスを比較する < 数\>文字列リテラル「112-111-1111」する要素。 特定の顧客の特定の電話番号がドキュメント内に存在するかどうかを判断するために、AdditionalContactInfo 列の電話番号の素のシーケンスがクエリで比較されます。  
  
```  
WITH XMLNAMESPACES (  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.value('         
   /aci:AdditionalContactInfo//act:telephoneNumber/act:number = "112-111-1111"', 'nvarchar(10)') as Result         
FROM Person.Contact         
WHERE ContactID=1         
```  
  
 クエリから True が返されます。 これは、その数字がドキュメント内に存在することを示します。 次のクエリは、前のクエリを少し変更したものです。 このクエリでは、ドキュメントから取得された電話番号の値が、2 つの電話番号の値のシーケンスと比較されます。 比較が True の場合、< 数\>要素が返されます。  
  
```  
WITH XMLNAMESPACES (  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.query('         
  if (/aci:AdditionalContactInfo//act:telephoneNumber/act:number = ("222-222-2222","112-111-1111"))         
  then          
     /aci:AdditionalContactInfo//act:telephoneNumber/act:number         
  else         
    ()') as Result         
FROM Person.Contact         
WHERE ContactID=1  
  
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
  
## <a name="value-comparison-operators"></a>値の比較演算子  
 値の比較演算子は、アトミック値を比較するために使用されます。 クエリ内では値の比較演算子の代わりに、一般的な比較演算子を使用できます。  
  
 値の比較演算子を次の表に定義します。  
  
|演算子|Description|  
|--------------|-----------------|  
|eq|等号|  
|ne|等しくないです。|  
|lt|より小さい|  
|gt|より大きい|  
|le|以下|  
|ge|以上|  
  
 選択された演算子に応じて 2 つの値の比較結果が同じになる場合、式は True を返します。 それ以外の場合は False を返します。 いずれかの値が空のシーケンスの場合、式の結果は False になります。  
  
 これらの演算子は、単一のアトミック値でのみ機能します。 つまり、オペランドの 1 つにシーケンスを指定することはできません。  
  
 たとえば、次のクエリを取得\<画像 > 要素、写真のサイズがここでは、製品モデルに対して"小さな。  
  
```  
SELECT CatalogDescription.query('         
              declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";         
              for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]         
              return         
                    $P         
             ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=19         
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   `declare namespace`クエリでは、使用する名前空間プレフィックスを定義します。  
  
-   \<サイズ > 要素の値が、指定したアトミック値"small"と比較します。  
  
-   値の演算子がアトミック値でのみ機能するため、 **data()**関数が暗黙的に使用をノードの値を取得します。 つまり、`data($P/PD:Size) eq "small"` も同じ結果になります。  
  
 結果を次に示します。  
  
```  
\<PD:Picture   
  xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  \<PD:Angle>front\</PD:Angle>  
  \<PD:Size>small\</PD:Size>  
  \<PD:ProductPhotoID>31\</PD:ProductPhotoID>  
\</PD:Picture>  
```  
  
 値の比較でのデータ型の上位変換の規則は、一般的な比較でのデータ型の上位変換の規則と同じです。 また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]一般的な比較の際に使用は、値の比較時に型指定されていない値に対して同じキャストの規則を使用します。 それに対して、XQuery 仕様の規則では、値の比較時に型指定されていない値は xs:string に常にキャストされます。  
  
## <a name="node-comparison-operator"></a>ノードの比較演算子  
 ノードの比較演算子、**は**ノード型にのみ適用されます。 返される結果は、基になるドキュメント内の同じノードを表すオペランドとして、2 つのノードが渡されたかどうかを示します。 2 つのオペランドが同じノードの場合、この演算子は True を返します。 それ以外の場合、False を返します。  
  
 次のクエリでは、特定の製品モデルの製造プロセス内で、ワーク センター拠点 10 がプロセスの最初にあるかどうかがチェックされます。  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' AS AWMI)  
  
SELECT ProductModelID, Instructions.query('         
    if (  (//AWMI:root/AWMI:Location[@LocationID=10])[1]         
          is          
          (//AWMI:root/AWMI:Location[1])[1] )          
    then         
          <Result>equal</Result>         
    else         
          <Result>Not-equal</Result>         
         ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=7           
```  
  
 結果を次に示します。  
  
```  
ProductModelID       Result          
-------------- --------------------------  
7              <Result>equal</Result>      
```  
  
## <a name="node-order-comparison-operators"></a>ノード順の比較演算子  
 ノード順の比較演算子により、ドキュメント内の位置に基づいて、ノードの組み合わせが比較されます。  
  
 ドキュメント内の表示順に基づいて行われる比較は次のようになります。  
  
-   `<<`: は**オペランド 1**前**オペランド 2**ドキュメント順でします。  
  
-   `>>`: は**オペランド 1**に従って**オペランド 2**ドキュメント順でします。  
  
 次のクエリは、製品カタログの説明がある場合に True を返します、\<保証 > 要素の前に、\<メンテナンス > 特定の製品ドキュメント順で要素です。  
  
```  
WITH XMLNAMESPACES (  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
  'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM)  
  
SELECT CatalogDescription.value('  
     (/PD:ProductDescription/PD:Features/WM:Warranty)[1] <<   
           (/PD:ProductDescription/PD:Features/WM:Maintenance)[1]', 'nvarchar(10)') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **Value()**のメソッド、 **xml**データ型は、クエリで使用します。  
  
-   クエリのブール型の結果に変換される**nvarchar (10)**返されるとします。  
  
-   クエリから True が返されます。  
  
## <a name="see-also"></a>参照  
 [型システムと #40 です。XQuery と #41 です。](../xquery/type-system-xquery.md)   
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
