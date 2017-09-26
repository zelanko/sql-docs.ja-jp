---
title: "以前のリリースの SQL Server Data Tools (SSDT と SSDT-BI) | Microsoft Docs"
ms.custom: 
ms.date: 07/28/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: fbd9bb9d0edbbeae81ebc074f28386476fd8635f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi"></a>以前のリリースの SQL Server Data Tools (SSDT と SSDT-BI)

SQL Server Data Tools (SSDT) には、SQL Server のコンテンツ タイプ (リレーショナル データベース、Analysis Services モデル、Reporting Services レポート、および Integration Services パッケージ) を構築するためのプロジェクト テンプレートとデザイン サーフェイスが収録されています。  
  
このツールは Visual Studio シェルが基になっており、SQL Server と共にリリースされます。 SSDT の新しいバージョンは、SQL Server の最新の機能と連携します。 古いバージョンに含まれているテンプレートと設計環境は、そのリリースの時点で最新であったものです。  
  
SSDT には後方互換性があるため、[最新の SSDT](/sql-docs/docs/ssdt/download-sql-server-data-tools-ssdt) でも古いバージョンの SQL Server を実行するデータベース、モデル、レポート、パッケージの設計と配置を行うことができます。  
  
> [!NOTE]  
> SQL Server のコンテンツ タイプの作成に使用される Visual Studio シェルは、これまでにさまざまな名前でリリースされてきました。たとえば、 **SQL Server Data Tools**、 **SQL Server Data Tools - Business Intelligence**、 **Business Intelligence Development Studio**です。 以前のバージョンに付属しているプロジェクト テンプレート セットの内容は、バージョンごとに異なります。 すべてのプロジェクト テンプレートを 1 つの SSDT でまとめて入手するには、 [最新バージョン](/sql-docs/docs/ssdt/download-sql-server-data-tools-ssdt)が必要です。 最新バージョンがない場合は、以前のバージョンをいくつもインストールしなければ、SQL Server で使われるテンプレートのすべてをそろえることはできません。  インストールされるシェルは、Visual Studio のバージョンごとに 1 つだけです。別のバージョンの SSDT をインストールすると、不足しているテンプレートだけが追加されます。  

## <a name="recent-downloads"></a>最近のダウンロード

[最新のリリース](download-sql-server-data-tools-ssdt.md)で問題が発生した万一の場合に備えて、最近の 3 つのダウンロードが提供されています。 

|リリース| Visual Studio 2015|Visual Studio 2013|
|:---|:---|:---|
|17.1|[SSDT for VS2015 17.1](https://go.microsoft.com/fwlink/?linkid=849393)| \* 該当なし|
|17.0|[SSDT for VS2015 17.0](https://go.microsoft.com/fwlink/?linkid=846626)| \* 該当なし|
|16.5|[SSDT for VS2015 16.5](https://go.microsoft.com/fwlink/?LinkID=832313)|[SSDT for VS2013 16.5](https://go.microsoft.com/fwlink/?LinkID=832308)|

\* SSDT は、Visual Studio の 2 つの最新バージョンをサポートしています。 Visual Studio 2017 のリリースにより、SSDT for VS2013 は今後更新されません。 詳細については、[この SSDT チームのブログ投稿](https://blogs.msdn.microsoft.com/ssdt/2017/03/10/sql-server-data-tools-17-0-rc-and-ssdt-in-vs2017/)で *FAQ* のセクションをご覧ください。

  
## <a name="links-to-download-pages"></a>ダウンロード ページへのリンク 
**SQL リレーショナル: データベース エンジン**  
  
RDBMS および Azure SQL Database 用のリレーショナル データベースを構築するためのテンプレートが収録されています。 SSDT は、リレーショナル データベース設計に関してはバージョンへの依存はありません。 Visual Studio 2012 と 2013 のどちらのバージョンも、SQL Server データベース エンジンや Azure SQL Database の任意のバージョンと共に使うことができます。  
  
**データベース デザイナー**  
  
-   [SSDT for Visual Studio 2013 のダウンロード](https://msdn.microsoft.com/dn864412)  
  
-   [SSDT for Visual Studio 2012 のダウンロード](https://msdn.microsoft.com/jj650015)  
  
-   **Visual Studio 2010 用 SSDT** は使用できなくなりました。新しいバージョンを選択してください。 新しいバージョンの SSDT は、インストールされている既存の Visual Studio 2010 と side-by-side 実行ができます。 SSDT と Visual Studio の製品版バージョンがコンピューター上で一致している必要はありません。  
  
Visual Studio 2013 を購入済みの場合は、プレビュー バージョンの SSDT をダウンロードして、まだ製品リリース バージョンにはない新しい機能を試すことができます。  
  
**SQL BI: Analysis Services、Reporting Services、Integration Services**  
  
BI のテンプレートは、SSAS モデル、SSRS レポート、SSIS パッケージの作成に使用されます。 BI デザイナーの各バージョンは、特定のリリースの SQL Server に対応しています。 BI の新しい機能を使うには、新しいバージョンの BI デザイナーをインストールしてください。  
  
**BI デザイナー**  
  
[SSDT-BI for Visual Studio 2013 のダウンロード](https://www.microsoft.com/download/details.aspx?id=42313) (SQL Server 2014、SQL Server 2012、SQL Server 2008、および 2008 R2)  
  
[SSDT-BI for Visual Studio 2012 のダウンロード](https://www.microsoft.com/download/details.aspx?id=36843) (SQL Server 2014、SQL Server 2012、SQL Server 2008、および 2008 R2)  
  
Business Intelligence Development Studio (BIDS) は SQL Server のセットアップを通じてインストールされます。 Web からダウンロードすることはできません。 (SQL Server 2008、および 2008 R2)  
  
SQL Server 2012 または 2014 の場合は、 **Visual Studio 2012 用 SSDT-BI** と **SSDT-BI と Visual Studio 2013**です。 この 2 つの違いは、Visual Studio のバージョンだけです。  
  
## <a name="see-also"></a>参照  
[SQL Server Data Tools &#40;SSDT&#41; のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)  
[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  
[SQL ツールとユーティリティ](../tools/overview-sql-tools.md)

