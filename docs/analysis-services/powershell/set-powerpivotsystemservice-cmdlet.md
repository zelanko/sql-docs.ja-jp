---
title: "Set-PowerPivotSystemService コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f6ef197b-3d74-4339-ae73-8a7c1eaf0e91
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Set-PowerPivotSystemService コマンドレット
  PowerPivotSystemService オブジェクトのグローバル プロパティをファームレベルで設定します。  
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## 構文  
  
```  
Set-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [-UpdateAssemblyInformation <switch>] [-WorkbookUpgradeOnDataRefresh <boolean>] [-DirectTCPConnections <boolean>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 Set-PowerPivotSystemService コマンドレットは、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスの親オブジェクトのプロパティを更新します。  
  
## パラメーター  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 プロパティを更新する親オブジェクトを指定します。 値は、ファーム内のオブジェクトを一意に識別する有効な GUID である必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -UpdateAssemblyInformation \<switch>  
 アップグレードの目的にのみ使用します。 SharePoint 構成データベースに格納されているバージョンと、ファームに配置されているアセンブリ バージョンが異なる場合、このコマンドレットを実行して構成データベース内のアセンブリ情報を更新できます。 アセンブリのバージョン情報は、グローバル アセンブリに格納されている Microsoft.AnalysisServices.SharePoint.Integration.dll のファイル プロパティで利用可能です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -WorkbookUpgradeOnDataRefresh \<boolean>  
 サーバーの定期データ更新の開始時に [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ブックを自動的にアップグレードするために使用します。 データ更新は、サーバーの現在のバージョンに対応するブックに対してのみサポートされます。 このプロパティを有効にする場合は、データ更新を続けることができるように、ブックが自動的にアップグレードされます。 このプロパティは、サーバー インスタンス レベルで設定されます。 特定のブック、ライブラリ、サイト、またはユーザーによって変えることはできません。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|2|  
|既定値|オプション|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -DirectTCPConnections \<boolean>  
 Excel Services が、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースに送信された各クエリ要求に使用される MSOLAP データ プロバイダーおよびチャネル転送をバイパスして、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースを読み込む SQL Server Analysis Services (POWERPIVOT) のインスタンスにすべてのクエリを直接送信するように指定します。  
  
 このパラメーターを設定すると、読み込まれたデータベースへの接続がより効率的になり、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリのパフォーマンスとスケーラビリティが向上します。 このパラメーターは、最初の読み込み要求の割り当て動作は変更しません。 ファーム内の複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint インスタンス間でデータベース読み込み要求を割り当てるために使用される他のパラメーター (–RoundRobinAllocation や –HealthBasedAllocation など) は影響を受けません。–DirectTCPConnections は、データベースが読み込まれた後に発行されるクエリのみに適用されるためです。  
  
 別々のアプリケーション サーバーで実行される Excel Services および [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を含むファーム トポロジでは、ファイアウォールのポートを開き、要求が SQL Server Analysis Services (POWERPIVOT) インスタンスに到達するようにする必要があります。 Analysis Services の名前付きインスタンスの着信接続を有効にする方法の詳細については、「[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を参照してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|3|  
|既定値|オプション|  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### -Confirm \<switch>  
 コマンドを実行する前に確認メッセージを表示します。 既定では、この値は有効にされています。 コマンドで確認応答を省略するには、コマンドで Confirm:$false を指定してください。  
  
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
C:\PS>Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true  
```  
  
 以前のバージョンのブックの自動アップグレードを有効にして、定期データ更新を続行できるようにします。  
  
  