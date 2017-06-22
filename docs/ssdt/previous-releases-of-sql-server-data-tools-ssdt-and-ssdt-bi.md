---
title: "以前のリリースの SQL Server Data Tools (SSDT と SSDT-BI) | Microsoft Docs"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d32e301-0f44-4916-b0db-76e8322c0ab7
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 16a6e0bce020b3108901d3a8fa08ecdf30475afe
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi"></a>以前のリリースの SQL Server Data Tools (SSDT と SSDT-BI)
SQL Server Data Tools (SSDT) には、SQL Server のコンテンツ タイプ (リレーショナル データベース、Analysis Services モデル、Reporting Services レポート、および Integration Services パッケージ) を構築するためのプロジェクト テンプレートとデザイン サーフェイスが収録されています。  
  
このツールは Visual Studio シェルが基になっており、SQL Server と共にリリースされます。 SSDT の新しいバージョンは、SQL Server の最新の機能に対応しています。 古いバージョンに含まれているテンプレートと設計環境は、そのリリースの時点で最新であったものです。  
  
SSDT には後方互換性があるため、 [最新の SSDT](https://msdn.microsoft.com/library/mt204009.aspx) でも古いバージョンの SQL Server を実行するデータベース、モデル、レポート、パッケージの設計とデプロイを行うことができます。 さらに、下記の以前リリースされたバージョンも使用可能です。  
  
> [!NOTE]  
> SQL Server のコンテンツ タイプの作成に使用される Visual Studio シェルは、これまでにさまざまな名前でリリースされてきました。たとえば、 **SQL Server Data Tools**、 **SQL Server Data Tools - Business Intelligence**、 **Business Intelligence Development Studio**です。 以前のバージョンに付属しているプロジェクト テンプレート セットの内容は、バージョンごとに異なります。 すべてのプロジェクト テンプレートを 1 つの SSDT でまとめて入手するには、 [最新バージョン](https://msdn.microsoft.com/library/mt204009.aspx)が必要です。 最新バージョンがない場合は、以前のバージョンをいくつもインストールしなければ、SQL Server で使われるテンプレートのすべてをそろえることはできません。  インストールされるシェルは、Visual Studio のバージョンごとに 1 つだけです。別のバージョンの SSDT をインストールすると、不足しているテンプレートだけが追加されます。  

## <a name="recent-downloads"></a>最近のダウンロード

[最新のリリース](https://msdn.microsoft.com/library/mt204009.aspx)で問題が発生した万一の場合に備えて、最近の 3 つのダウンロードが提供されています。 

|リリース| Visual Studio 2015|Visual Studio 2013|
|:---|:---|:---|
|16.5|[SSDT for VS2015 16.5](https://go.microsoft.com/fwlink/?LinkID=832313)|[SSDT for VS2013 16.5](https://go.microsoft.com/fwlink/?LinkID=832308)|
|16.4.1|[SSDT for VS2015 16.4.1](https://go.microsoft.com/fwlink/?LinkID=828740)|[SSDT for VS2013 16.4.1](https://go.microsoft.com/fwlink/?LinkID=828737)|
|16.3|[SSDT for VS2015 16.3](https://go.microsoft.com/fwlink/?LinkID=824659)|[SSDT for VS2013 16.3](https://go.microsoft.com/fwlink/?LinkID=824656)|



  
## <a name="links-to-download-pages"></a>ダウンロード ページへのリンク  
**SQL リレーショナル: データベース エンジン**  
  
RDBMS および Azure SQL Database 用のリレーショナル データベースを構築するためのテンプレートが収録されています。 SSDT は、リレーショナル データベース設計に関してはバージョンへの依存はありません。 Visual Studio 2012 と 2013 のどちらのバージョンも、SQL Server データベース エンジンや Azure SQL Database の任意のバージョンと共に使うことができます。  
  
**データベース デザイナー**  
  
-   [SSDT for Visual Studio 2013 のダウンロード](https://msdn.microsoft.com/dn864412)  
  
-   [SSDT for Visual Studio 2012 のダウンロード](https://msdn.microsoft.com/jj650015)  
  
-   **Visual Studio 2010 用 SSDT** は使用できなくなりました。新しいバージョンを選択してください。 新しいバージョンの SSDT は、既存の Visual Studio 2010 のインストールと同時に実行できます。 SSDT と Visual Studio の製品版バージョンがコンピューター上で一致している必要はありません。  
  
Visual Studio 2013 を購入済みの場合は、プレビュー バージョンの SSDT をダウンロードして、まだ製品リリース バージョンにはない新しい機能を試すことができます。  
  
**SQL BI: Analysis Services、Reporting Services、Integration Services**  
  
BI のテンプレートは、SSAS モデル、SSRS レポート、SSIS パッケージの作成に使用されます。 BI デザイナーの各バージョンは、特定のリリースの SQL Server に対応しています。 BI の新しい機能を使うには、新しいバージョンの BI デザイナーをインストールしてください。  
  
**BI デザイナー**  
  
[SSDT-BI for Visual Studio 2013 のダウンロード](https://www.microsoft.com/download/details.aspx?id=42313): SQL Server 2014、SQL Server 2012、SQL Server 2008 および 2008 R2  
  
[SSDT-BI for Visual Studio 2012 のダウンロード](https://www.microsoft.com/download/details.aspx?id=36843): SQL Server 2014、SQL Server 2012、SQL Server 2008 および 2008 R2  
  
Business Intelligence Development Studio (BIDS) - BIDS は SQL Server のセットアップを通じてインストールされます。 Web ダウンロードはありません: SQL Server 2008 および 2008 R2  
  
SQL Server 2012 または 2014 の場合は、 **Visual Studio 2012 用 SSDT-BI** と **SSDT-BI fと Visual Studio 2013**です。 この 2 つの違いは、Visual Studio のバージョンだけです。  
  
## <a name="see-also"></a>参照  
[SQL Server Data Tools &#40;SSDT&#41; のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)  
[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  
  

