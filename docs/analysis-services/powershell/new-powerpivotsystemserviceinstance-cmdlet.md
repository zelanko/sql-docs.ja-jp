---
title: "New-PowerPivotSystemServiceInstance コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7ea94113-c0f1-4cca-9228-f1a034fba5db
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# New-PowerPivotSystemServiceInstance コマンドレット
  新しいインスタンスを追加 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をアプリケーション サーバーのシステム サービスです。  
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## 構文  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## Description  
 New-PowerPivotSystemServiceInstance コマンドレットは、SQL Server セットアップを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をローカル アプリケーション サーバーにインストールした後に、ファーム レベルで新しい PowerPivotSystemService オブジェクトをプロビジョニングします。 各アプリケーション サーバーにサービス インスタンスを 1 つだけ作成できます。  サービスが既に準備されている場合は、このコマンドレットを実行することはできません。  
  
## パラメーター  
  
### -ParentService \<PowerPivotMidTierServicePipeBind>  
 GUID を指定、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のシステム サービスの親オブジェクトです。 このリリースでは、1 つの親オブジェクトのみが許可されます。 Get-PowerPivotSystemService を使用してサービス オブジェクトまたはその GUID を返すことができます。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -SystemServiceInstanceName \<string>  
 このオブジェクトを識別する名前を指定します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### Provision [\<SwitchParameter>]  
 SharePoint でサービスを利用できるようにします。 有効な値は $true または $false です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### \<CommonParameters>  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「[About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## 入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## 例 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 この例は、コマンドレットの最も一般的な形式を示します。 登録、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] と、ファームのローカル アプリケーション サーバー上のシステム サービスです。  
  
## 例 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 この例の名前、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスのインスタンスがそれをプロビジョニングします。 名前を指定しない場合は、既定の名前である SQL Server Analysis Services System サービス インスタンスが使用されます。 サービスのカスタム名を作成するのはオプションです。 テスト シナリオをサポートするために、または、後の手順でインスタンスを準備するためのカスタム ツールまたはスクリプトを持っている場合、サービスに名前を付けることができます。  
  
  