---
title: New-powerpivotsystemserviceinstance コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b5d24b48d2c7b68f7408b5a3ad1da224cc992c3e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-powerpivotsystemserviceinstance-cmdlet"></a>New-PowerPivotSystemServiceInstance コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  新しいインスタンスを追加 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をアプリケーション サーバーのシステム サービスです。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 New-PowerPivotSystemServiceInstance コマンドレットは、SQL Server セットアップを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をローカル アプリケーション サーバーにインストールした後に、ファーム レベルで新しい PowerPivotSystemService オブジェクトをプロビジョニングします。 各アプリケーション サーバーにサービス インスタンスを 1 つだけ作成できます。  サービスが既に準備されている場合は、このコマンドレットを実行することはできません。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-parentservice-powerpivotmidtierservicepipebind"></a>-ParentService \<PowerPivotMidTierServicePipeBind>  
 GUID を指定、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のシステム サービスの親オブジェクトです。 このリリースでは、1 つの親オブジェクトのみが許可されます。 Get-PowerPivotSystemService を使用してサービス オブジェクトまたはその GUID を返すことができます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-systemserviceinstancename-string"></a>-SystemServiceInstanceName \<string>  
 このオブジェクトを識別する名前を指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="provision-switchparameter"></a>プロビジョニング [\<SwitchParameter >]  
 SharePoint でサービスを利用できるようにします。 有効な値は $true または $false です。  
  
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
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 この例は、コマンドレットの最も一般的な形式を示します。 登録、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] と、ファームのローカル アプリケーション サーバー上のシステム サービスです。  
  
## <a name="example-2"></a>例 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 この例の名前、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスのインスタンスがそれをプロビジョニングします。 名前を指定しない場合は、既定の名前である SQL Server Analysis Services System サービス インスタンスが使用されます。 サービスのカスタム名を作成するのはオプションです。 テスト シナリオをサポートするために、または、後の手順でインスタンスを準備するためのカスタム ツールまたはスクリプトを持っている場合、サービスに名前を付けることができます。  
  
  
