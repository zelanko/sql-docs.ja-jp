---
title: "Analysis Services での表形式モデルの互換性レベル | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.versioncompat.f1"
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Analysis Services での表形式モデルの互換性レベル
  モデルまたはデータベースの "*互換性レベル*" とは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エンジンでのリリース固有の一連の動作を意味します。 サポートされている互換性レベルでモデルを作成することで、特定のリリースの動作を取得できます。 たとえば、DirectQuery と表形式オブジェクトのメタデータは、互換性レベルの割り当てによって実装が異なります。  
  
 **SQL Server 2016 RTM (1200)**、つまり互換性レベル 1200 は SQL Server 2016 の新しい互換性レベルであり、表形式モデルにのみ適用されます。  互換性レベル 1200 の表形式モデルは、 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 表形式インスタンスでのみ動作します。  
  
 表形式モデルを作成またはアップグレードするには、SQL Server Data Tools (SSDT) を使用し、プロジェクトの作成時に **[互換性レベル]** プロパティを設定するか、プロジェクトの作成後に **model.bim** ファイルでこのプロパティを設定します。  
  
> [!NOTE]  
>  多次元モデルでは、互換性レベルに関しては独立したバージョン パスに従います。 1103 の場合と同様に、番号が同じであっても、これは偶然の一致です。 詳細については、「[多次元データベースの互換性レベル &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)」を参照してください。  
  
## 表形式モデル データベースのサポートされる互換性レベル  
 Analysis Services は、次の互換性レベルをサポートします。これは、モデルとデータベースの両方に適用されます。  より高い互換性レベルが使用できるかどうかは、モデルを作成するためのツールのバージョンによって決まります。  
  
||||  
|-|-|-|  
|互換性レベル|サーバーのバージョン|モデリング ツールのバージョン|  
|1200|SQL Server 2016 インスタンスのみで動作|[Visual Studio 2015 用 SQL Server Data Tools のみ](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> このレベルで使用できる機能については、「[What's New in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md) 」を参照してください。|  
|1103|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1|[Visual Studio 2015 用 SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>2</sup><br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)|  
|1100|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1<br /><br /> SQL Server 2012|[Visual Studio 2015 用 SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)<br /><br /> Business Intelligence Development Studio (Visual Studio 2010 シェルで動作し、SQL Server セットアップを使用してインストール)|  
  
 <sup>1</sup> Visual Studio 2015 用 SQL Server Data Tools を使用して 1100 または 1103 表形式モデルを Analysis Services の以前のリリースに展開できます。  
  
 <sup>2</sup> 互換性レベル 1100、1103、および 1200 は Visual Studio 2015 用 SQL Server Data Tools のテーブル モデル プロジェクトで有効ですが、1200 モデルは Analysis Services の SQL Server 2016 インスタンス上でのみ展開および実行することができます。  
  
## SSDT で表形式を作成またはアップグレードするときに互換性レベルを設定する  
 SQL Server Data Tools (SSDT) で新しい表形式モデル プロジェクトを作成するときに、**[新しい表形式プロジェクトのオプション]** ダイアログ ボックスで互換性レベルを指定できます。  
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.jpg "ssas_tabularproject_compat1200")  
  
 **[今後、このメッセージを表示しない]** オプションを選択することで、既定の互換性レベルを指定することもできます。 以降、すべてのプロジェクトで、指定した互換性レベルが使用されます。 SSDT の既定の互換性レベルは、**[ツール]**、**[オプション]** の順に選択すると変更できます。  
  
 表形式モデル プロジェクトをアップグレードするには、モデルの **[プロパティ]** ウィンドウの **[互換性レベル]** プロパティを **[SQL Server 2016 RTM (1200)]** に設定します。  詳細については、「 [Upgrade Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) 」をご覧ください。  
  
> [!NOTE]  
>  表形式モデルを作成する方法の 1 つは、インポートされた Power Pivot ブックを使用することです。 既定では、Power BI Desktop は、互換性レベル 1200 で表形式モデルを自動的に作成します。 ただし、以前のバージョンの Power Pivot ブックは、1100 レベルである可能性があります。 古いブックを使用する場合は、 **[互換性レベル]** プロパティを変更してアップグレードしてください。  
  
## SSMS でデータベースの互換性レベルを確認する  
 SSMS で、データベースを右クリックし、**[プロパティ]**、**[互換性レベル]** の順にクリックします。  
  
## SSMS でサーバーのサポートされる互換性レベルを確認する  
 SSMS で、サーバー名を右クリックし、**[プロパティ]**、**[サポートされる互換性レベル]** の順にクリックします。  
  
 このプロパティは、サーバーで実行されるデータベースの最上位の互換性レベルを指定します。  サポートされる互換性レベルは読み取り専用であり、変更できません。  
  
## 参照  
 [多次元データベースの互換性レベル &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Analysis Services の新機能](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Power Pivot からのインポート &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [新しいテーブル モデル プロジェクトを作成する &#40;Analysis Services&#41;](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  