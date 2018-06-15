---
title: Get-powerpivotserviceapplication コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a5ccd05b8c5e947972218a22c0abbc358731ee5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027872"
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Get-PowerPivotServiceApplication コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind>  
 取得するサービス アプリケーションを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID である必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
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
  
  
