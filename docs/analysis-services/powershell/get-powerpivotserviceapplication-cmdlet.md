---
title: "Get-powerpivotserviceapplication コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c96b18bb421d264c99a683af04a51d6e60597d3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Get-PowerPivotServiceApplication コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  1 つまたは複数の返します [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Get-PowerPivotServiceApplication コマンドレットは、Identity パラメーターで指定されたサービス アプリケーションを返します。 コマンドレットに、すべてを返しますパラメーターが指定されていない場合 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のアプリケーションのサービスを提供します。 各アプリケーションは、その表示名、アプリケーションの種類、および GUID によって識別されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの追加のプロパティを表示するには、コマンドレットに format-list オプションを追加します。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>Id \<SPGeminiServiceApplicationPipeBind >  
 取得するサービス アプリケーションを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID である必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 この例では、ファーム内の 1 つ以上のサービス アプリケーションを返します。  
  
## <a name="example-2"></a>例 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 この例では、すべてのプロパティを返します、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。  
  
## <a name="example-3"></a>例 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 この例では、1 つのサービス アプリケーションを返し、表示名、アプリケーションの種類、およびアプリケーションの GUID を表示します。 表示名が長い場合は、切り捨てられます。 format-list オプションを使用すると完全名が表示されます。  
  
  
