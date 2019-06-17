---
title: どのような&#39;s New in Analysis Services と Business Intelligence |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 173ca9fbf1fa3e9e2dc9dcb177c45a2ea3849415
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66065314"
---
# <a name="what39s-new-in-analysis-services-and-business-intelligence"></a>どのような&#39;s New in Analysis Services と Business Intelligence
  多次元のモデルに対する Power View レポートをサポートしている機能が追加の例外で[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]以前のリリースから変更されていません。  
  
 については、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]製品およびテクノロジは、このリリースでは異なる「 [SQL Server 2014 における新](../sql-server/what-s-new-in-sql-server-2016.md)します。  
  
## <a name="updates-to-design-tool-installation"></a>デザイン ツールのインストールに対する更新  
 以前は Business Intelligence Development Studio (BIDS) と呼ばれていた、ビジネス インテリジェンス用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (SSDT-BI) を使用して、Analysis Services モデル、Reporting Services レポート、および Integration Services パッケージを作成できます。 次の場所から SSDT-BI をダウンロードできます。  
  
-   [Visual Studio 2013 用 SSDT-BI をダウンロードします。](https://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Visual Studio 2012 用 SSDT-BI をダウンロードします。](https://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 SSDT-BI または BIDS の以前のバージョンをコンピューターにインストールしていた場合は、新しいバージョンが以前のバージョンと共にサイド バイ サイドでインストールされます。 サーバーの特定のバージョンに関連付けられているプロジェクトとソリューションを変更できるように、1 台のワークステーションでデザイン ツールの新しいバージョンと以前のバージョンを実行することは一般的です。  
  
> [!NOTE]  
>  SSDT の Visual Studio 2012 バージョンと Visual Studio 2013 バージョンを入手できるダウンロード サイトは複数存在します。 ほとんどのダウンロードには、BI プロジェクト テンプレートが含まれていません。 上記のリンクを使用すると、適切なバージョンを取得できます。 Business Intelligence プロジェクト テンプレート フォルダーを表示する場合、SSDT BI の正しいバージョンがあることがわかります。 このフォルダーには、Analysis Services、Reporting Services、および Integration Services 用のプロジェクト テンプレートが格納されています。 SSDT-BI をインストールした方法によっては、SQL Server データベース用の追加のプロジェクト テンプレートも表示されることがあります。  
  
 ![SSDT の新しいプロジェクト テンプレート](media/ssdt-biprojects.png "SSDT の新しいプロジェクト テンプレート")  
  
## <a name="features-recently-added-power-view-for-multidimensional-models"></a>最近追加された機能:多次元モデルの Power View  
 多次元モデルに対応する Power View レポートを作成する機能は、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 1 Cumulative Update 4 で最初に導入されました。 多次元モデルの Power View 機能は、現在では製品の一部として [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] に含まれています。  
  
 **多次元モデルの power View レポート**  
  
 ![Power View レポート](media/powerviewreport-wn.gif "Power View レポート")  
  
 この機能は、多次元モデル (OLAP キューブとも呼びます) を最新のレポート クライアント ツールで使用できるようにするため、組織が BI への既存の投資を最大限に活用するうえで役立ちます。 多次元モデル内のデータの種類に応じて、テーブルやマトリックスから、バブル チャートや地理的マップまで、さまざまな動的視覚エフェクトを簡単に作成できます。 また、多次元モデルは、Data Analysis Expressions (DAX) を使用するクエリをサポートするようになりました。  
  
 多次元モデルの power View での組み込みの Power View レポート機能を必要と[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SharePoint モード) では。 Power View の他のバージョン、特に Excel 2013 の Power View アドインは、多次元モデルをサポートしません。  
  
 詳細についてを参照してください。[多次元モデルの Power View](https://msdn.microsoft.com/library/dn140246.aspx)します。  
  
  
