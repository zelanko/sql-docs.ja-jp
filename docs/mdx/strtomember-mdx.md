---
title: "StrToMember (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRTOMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToMember function
ms.assetid: eb8a3dc0-5ae4-434e-b321-680a81a59e67
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1b87517d73298dbc837d5659ac18b967c45aeaf7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="strtomember-mdx"></a>StrToMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多次元式 (MDX) 形式の文字列によって指定されているメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 直接的または間接的にメンバーを指定する有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **StrToMember**関数、文字列式で指定されたメンバーを返します。 **StrToMember**関数は、通常使用ユーザー定義関数またはを返す、メンバー指定を外部関数から MDX ステートメントでは、MDX クエリがパラメーター化されたときにします。  
  
-   CONSTRAINED フラグを使用するときは、メンバー名には修飾されているメンバー名または修飾されていないメンバー名に直接解決できる文字列を指定する必要があります。 このフラグは、指定された文字列によるインジェクション攻撃の危険性を軽減するために使用します。 修飾されているメンバー名または修飾されていないメンバー名に直接解決できない文字列を指定すると、"STRTOMEMBER 関数の CONSTRAINED フラグによって設定された制限に違反しました。" というエラーが表示されます。  
  
-   CONSTRAINED フラグを使用しない場合、メンバー名に直接解決されるメンバーも、名前に解決される MDX 式に解決されるメンバーも指定できます。  
  
-   セットとメンバーの違いを理解するには、「セット式の使用」および「メンバー式の使用」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、Bayern メンバーの Reseller Sales Amount メジャーを返しますを使用して、State-province 属性階層で、 **StrToMember**関数。 文字列の指定により、修飾されているメンバー名が指定されています。  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例を使用して、Bayern メンバーの Reseller Sales Amount メジャーを返します、 **StrToMember**関数。 メンバー名文字列には修飾されていないメンバー名のみを指定したので、クエリは指定メンバーの最初のインスタンスを返します。この最初のインスタンスは、Reseller Sales と交差しない Customer ディメンションの Customer Geography 階層にあります。 期待する結果を確実に取得するには、修飾されている名前を指定することをお勧めします。  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例では、Bayern メンバーの Reseller Sales Amount メジャーを返しますを使用して、State-province 属性階層で、 **StrToMember**関数。 指定したメンバー名文字列は、修飾されているメンバー名に解決されます。  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 次の例では、CONSTRAINED フラグが原因でエラーが返されます。 指定したメンバー名文字列には、修飾されているメンバー名に解決される有効な MDX メンバー式が含まれていますが、CONSTRAINED フラグを使用しているので、メンバー名文字列内に修飾されているメンバー名または修飾されていないメンバー名が必要になります。  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

