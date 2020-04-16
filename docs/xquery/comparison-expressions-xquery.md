---
title: 比較式 (XQuery) |マイクロソフトドキュメント
description: 一般、値、ノード、およびノード順序の比較演算子を含む XQuery 比較式の使用方法について説明します。
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
- node comparison operators [XQuery]
- comparison expressions [XQuery]
- node order comparison operators [XQuery]
- expressions [XQuery], comparison
- comparison operators [XQuery]
- value comparison operators
ms.assetid: dc671348-306f-48ef-9e6e-81fc3c7260a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 082fb2d1afdfa8824ea6f3d6e7bd3e4c484e281e
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388165"
---
# <a name="comparison-expressions-xquery"></a>比較式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery には、次の種類の比較演算子が用意されています。  
  
-   一般的な比較演算子  
  
-   値比較演算子  
  
-   ノード比較演算子  
  
-   ノード順序比較演算子  
  
## <a name="general-comparison-operators"></a>一般的な比較演算子  
 一般的な比較演算子を使用して、アトミック値、シーケンス、またはその 2 つの組み合わせを比較できます。  
  
 一般的な演算子を次の表に定義します。  
  
|演算子|説明|  
|--------------|-----------------|  
|=|Equal|  
|!=|等しくない|  
|\<|より小さい|  
|>|より大きい|  
|\<=|以下|  
|>=|以上|  
  
 一般的な比較演算子を使用して 2 つのシーケンスを比較する場合、2 番目のシーケンスに True を最初のシーケンスの値と比較する値が存在すると、全体の結果は True になります。 それ以外の場合は False です。 たとえば、(1, 2, 3) = (3, 4) は両方のシーケンスに値 3 があるので True になります。  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3) = (3,4)')    
```  
  
 比較する 2 つの値の型は、比較できる型である必要があります。 具体的には、値の型は静的に確認されます。 数値の比較の場合、数値型の上位変換が発生する場合があります。 例えば、10 進数値 10 が 2 倍の値 1e1 と比較される場合、10 進値は倍精度浮動小数点数に変更されます。 double 値の比較は正確には行えないので、不正確な結果になる場合があります。  
  
 値の一方が型指定されていない場合は、もう一方の値の型にキャストされます。 次の例では、値 7 は整数として扱われます。 比較される前に、/a[1] の型指定されていない値は整数に変換されます。 整数の比較は True を返します。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < 7')  
```  
  
 逆に、型なしの値が文字列または他の型なし値と比較された場合、その値は xs:string にキャストされます。 次のクエリでは、文字列 6 が文字列 "17" と比較されます。 このクエリは文字列の比較になるので、False が返されます。  
  
```  
declare @x xml  
set @x='<a>6</a>'  
select @x.query('/a[1] < "17"')  
```  
  
 次のクエリは、AdventureWorks サンプル データベースに用意されている製品カタログから、製品モデルの小さな画像を返します。 クエリは、返されたアトミック値のシーケンス`PD:ProductDescription/PD:Picture/PD:Size`を、シングルトン シーケンス "small" と比較します。 比較が True の場合は、<ピクチャ\>要素を返します。  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('         
    for $P in /PD:ProductDescription/PD:Picture[PD:Size = "small"]         
    return $P') as Result         
FROM   Production.ProductModel         
WHERE  ProductModelID=19         
```  
  
 次のクエリは、<番号\>要素内の電話番号のシーケンスを文字列リテラル "112-111-1111" と比較します。 このクエリは、追加のContactInfo列の電話番号要素のシーケンスを比較して、特定の顧客の特定の電話番号がドキュメント内に存在するかどうかを判断します。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.value('         
   /aci:AdditionalContactInfo//act:telephoneNumber/act:number = "112-111-1111"', 'nvarchar(10)') as Result         
FROM Person.Contact         
WHERE ContactID=1         
```  
  
 クエリは True を返します。 これは、その数字がドキュメント内に存在することを示します。 次のクエリは、前のクエリの少し変更されたバージョンです。 このクエリでは、ドキュメントから取得した電話番号の値が、2 つの電話番号値のシーケンスと比較されます。 比較が True の場合、<\>番号要素が返されます。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
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
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
    112-111-1111  
\</act:number>   
```  
  
## <a name="value-comparison-operators"></a>値の比較演算子  
 値の比較演算子は、アトミック値を比較するために使用されます。 クエリでは、値の比較演算子の代わりに一般的な比較演算子を使用できます。  
  
 値の比較演算子は、次の表で定義されています。  
  
|演算子|説明|  
|--------------|-----------------|  
|eq|Equal|  
|ne|等しくない|  
|lt|より小さい|  
|gt|より大きい|  
|le|以下|  
|ge|以上|  
  
 2 つの値が選択された演算子に従って同じ値を比較する場合、式は True を返します。 それ以外の場合は False を返します。 いずれかの値が空のシーケンスの場合、式の結果は False になります。  
  
 これらの演算子は、単一のアトミック値でのみ機能します。 つまり、オペランドの 1 つにシーケンスを指定することはできません。  
  
 たとえば、次のクエリは\<、画像サイズが "小さい" である製品モデルの画像>要素を取得します。  
  
```  
SELECT CatalogDescription.query('         
              declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";         
              for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]         
              return         
                    $P         
             ') as Result         
FROM Production.ProductModel         
WHERE ProductModelID=19         
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   `declare namespace`は、後でクエリで使用される名前空間プレフィックスを定義します。  
  
-   \<size>要素の値は、指定された原子値 "small" と比較されます。  
  
-   値演算子はアトミック値でのみ動作するため **、data()** 関数はノード値の取得に暗黙的に使用されます。 つまり、`data($P/PD:Size) eq "small"` も同じ結果になります。  
  
 結果を次に示します。  
  
```  
\<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  \<PD:Angle>front\</PD:Angle>  
  \<PD:Size>small\</PD:Size>  
  \<PD:ProductPhotoID>31\</PD:ProductPhotoID>  
\</PD:Picture>  
```  
  
 値の比較でのデータ型の上位変換の規則は、一般的な比較でのデータ型の上位変換の規則と同じです。 また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]値の比較時に、一般的な比較で使用するのと同じキャスト規則を、型なし値に対して使用します。 それに対して、XQuery 仕様の規則では、値の比較時に型指定されていない値は xs:string に常にキャストされます。  
  
## <a name="node-comparison-operator"></a>ノード比較演算子  
 ノード比較演算子**は**、ノードタイプにのみ適用されます。 返される結果は、オペランドとして渡された 2 つのノードがソース ドキュメント内の同じノードを表しているかどうかを示します。 2 つのオペランドが同じノードである場合、この演算子は True を返します。 それ以外の場合は、False を返します。  
  
 次のクエリでは、ワーク センターの場所 10 が特定の製品モデルの製造プロセスの最初の場所であるかどうかを確認します。  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' AS AWMI)  
  
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
  
## <a name="node-order-comparison-operators"></a>ノード順序比較演算子  
 ノードの順序比較演算子は、ドキュメント内の位置に基づいて、ノードのペアを比較します。  
  
 ドキュメントの順序に基づいて行われる比較は次のとおりです。  
  
-   `<<`:**オペランド 1**は、文書順で**オペランド 2**の前に置かれます。  
  
-   `>>`:**オペランド 1**は、文書順の**オペランド 2**に続きます。  
  
 次のクエリは、製品カタログの説明に、特定\<の製品のドキュメント順の\<保守>要素の前に表示される保証>要素がある場合は、True を返します。  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM)  
  
SELECT CatalogDescription.value('  
     (/PD:ProductDescription/PD:Features/WM:Warranty)[1] <<   
           (/PD:ProductDescription/PD:Features/WM:Maintenance)[1]', 'nvarchar(10)') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   **xml**データ型の**value()** メソッドがクエリで使用されます。  
  
-   クエリのブール値の結果は**nvarchar(10)** に変換され、返されます。  
  
-   クエリは True を返します。  
  
## <a name="see-also"></a>参照  
 [システム&#40;XQuery&#41;の入力](../xquery/type-system-xquery.md)   
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
