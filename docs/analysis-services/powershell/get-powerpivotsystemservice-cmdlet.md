---
title: "Get-PowerPivotSystemService コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Get-PowerPivotSystemService コマンドレット
  グローバル プロパティを返す、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファームでのシステムのサービス オブジェクト。  
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## 構文  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 Get-PowerPivotSystemService コマンドレットは、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service オブジェクトのグローバル プロパティを返します。 ファームごとに 1 つの親オブジェクトがある、各ファームはの複数のインスタンスを持つことができますが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] システム サービスは、ファーム内の個々 のアプリケーション サーバー上で実行します。 親オブジェクトは、インスタンスによって異なることのない、ファームレベルの設定を示します。 ファームに複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint インストールが含まれている場合、インスタンスのコンマ区切りリストにより、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service インスタンスの数が示されます。  
  
## パラメーター  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 取得する親オブジェクトを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID である必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
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
C:\PS>Get-PowerPivotSystemService  
```  
  
 この例でのすべてのインスタンスで共有されるプロパティを表示、親オブジェクトのグローバル プロパティが返されます [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のシステム サービスです。  
  
  