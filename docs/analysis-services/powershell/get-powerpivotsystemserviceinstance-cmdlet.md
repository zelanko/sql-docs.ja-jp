---
title: Get-powerpivotsystemserviceinstance コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cb07d3ee84f8a43e15732f3aafc1a4c7cef83fbf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="get-powerpivotsystemserviceinstance-cmdlet"></a>Get-PowerPivotSystemServiceInstance コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  1 つまたは複数のインスタンスを返します [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のアプリケーション サーバーで実行されているシステム サービスです。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Get-powerpivotsystemserviceinstance コマンドレットは、1 つまたは複数のプロパティを返します [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス インスタンスがファームで実行されています。 このコマンドレットは、アプリケーションの種類、状態 (オンラインまたはオフライン)、および ID を報告します。 特定のインスタンスの追加のプロパティを表示するには、コマンドレットに Identity パラメーターと format-list オプションを追加します。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>Id \<PowerPivotMidTierServiceInstancePipeBind >  
 取得するサービス インスタンスを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID でなければなりません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」をご覧ください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 この例では、サーバー名、バージョン、アップグレードの状態など、指定したインスタンスの追加のプロパティを返します。  
  
  
