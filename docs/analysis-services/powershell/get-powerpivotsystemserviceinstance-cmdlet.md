---
title: "Get-PowerPivotSystemServiceInstance コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Get-PowerPivotSystemServiceInstance コマンドレット
  1 つまたは複数のインスタンスを返します [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のアプリケーション サーバーで実行されているシステム サービスです。  
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## 構文  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Get-powerpivotsystemserviceinstance コマンドレットは、1 つまたは複数のプロパティを返します [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービス インスタンスがファームで実行されています。 このコマンドレットは、アプリケーションの種類、状態 (オンラインまたはオフライン)、および ID を報告します。 特定のインスタンスの追加のプロパティを表示するには、コマンドレットに Identity パラメーターと format-list オプションを追加します。  
  
## パラメーター  
  
### -Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 取得するサービス インスタンスを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID でなければなりません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### \<CommonParameters>  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「[About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」をご覧ください。  
  
## 入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## 例 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 この例では、サーバー名、バージョン、アップグレードの状態など、指定したインスタンスの追加のプロパティを返します。  
  
  