---
title: Remove-powerpivotsystemserviceinstance コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c3f6f960d0f2b39fa877203ede26f5e66b5c3c37
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="remove-powerpivotsystemserviceinstance-cmdlet"></a>Remove-PowerPivotSystemServiceInstance コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス インスタンスをファームから削除します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Remove-PowerPivotSystemServiceInstance コマンドレットは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスに関するインスタンス情報をファームから削除します。 プログラム ファイルは削除しません。 プログラム ファイルを完全に削除するには、それらをアンインストールする必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを削除する場合は、関連する Analysis Services インスタンスを削除する Remove-PowerPivotEngineServiceInstance とPowerPivotservice アプリケーションを削除する Remove-PowerPivotServiceApplication も必ず実行してください。 サービスを削除すると、サービス アプリケーションを実行できなくなります。  
  
 この変更を元に戻すには、New-PowerPivotSystemServiceInstance -Provision:$true を実行してインスタンス情報を再度有効にします。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-identity-powerpivotmidtierserviceinstancepipebind"></a>Id \<PowerPivotMidTierServiceInstancePipeBind >  
 削除する [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス インスタンスの GUID を指定します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされているアプリケーション サーバーごとに 1 つのサーバー インスタンスがあります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-deletelocal-switch"></a>-DeleteLocal \<switch>  
 ローカル コンピューターにインストールされている [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスのインスタンスを削除します。これにより、オブジェクトの ID を指定しなくてもインスタンスを削除できます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-confirm-switch"></a>-Confirm \<switch>  
 コマンドを実行する前に確認メッセージを表示します。 既定では、この値は有効にされています。 コマンドで確認応答を省略するには、コマンドで Confirm:$false を指定してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
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
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 この例は、ローカル アプリケーション サーバーで実行されている [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスのインスタンスを削除する方法を示しています。  
  
## <a name="example-2"></a>例 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 この例では、特定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを、その ID に基づいて削除する方法を示しています。  
  
  
