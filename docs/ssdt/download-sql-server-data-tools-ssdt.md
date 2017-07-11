---
title: "SQL Server Data Tools (SSDT) のダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "ssdt のインストール, ssdt のダウンロード, 最新の ssdt"
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 5bd0e1d3955d898824d285d28979089e2de6f322
ms.openlocfilehash: 7aaa4c48419bf24357b2bef95c40d721d1ab2f2a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
<a id="download-sql-server-data-tools-ssdt" class="xliff"></a>

# SQL Server Data Tools (SSDT) のダウンロード

無料でダウンロードできる最新の開発ツールである **[SQL Server Data Tools](https://msdn.microsoft.com/mt186501)** を使用すると、SQL Server リレーショナル データベース、Azure SQL Database、Integration Services パッケージ、Analysis Services データ モデル、および Reporting Services レポートを作成できます。 SSDT では、Visual Studio でアプリケーションを開発する場合と同じくらい簡単に、SQL Server のコンテンツの種類を設計および展開できます。 このリリースでは、SQL Server 2005 から SQL Server 2017 までをサポートし、SQL Server 2016 の新機能を追加するためのデザイン環境を提供します。  
    
    
![ダウンロード](../ssdt/media/download.png) [Visual Studio 2015 用 SQL Server Data Tools 17.1 のダウンロード](https://go.microsoft.com/fwlink/?linkid=849393)

![ダウンロード](../ssdt/media/download.png) [データ層アプリケーション フレームワーク (DacFx) 17.1 のダウンロード](https://www.microsoft.com/download/details.aspx?id=55255)

<a id="sql-server-data-tools" class="xliff"></a>

## SQL Server Data Tools   
**バージョン情報**  
  
リリース番号: 17.1  
このリリースのビルド番号: 14.0.61705.170
  
 **新機能**
 - AS のモデルに関係がない IntelliSense のオフライン サポート (強調表示、ステートメントの完了、パラメーター情報など)
 - M 式を表示する表形式モデル エクスプローラーのへの追加
 - 表形式モデルでロール メンバーを構成する Azure Active Directory のユーザー選択ウィンドウ
 - 1,400 モデルを定義する場合に UI のヒントをエンコードするサポート
 - AS プロジェクトの複数のバグを修正
 - DacFx の複数のバグを修正

 **既知の問題**
 - 1,400 の互換性レベル AS モデルで新しいデータ ソースを作成するときに、ファイル ベースのデータ ソースを選択し、キャンセルを押してからデータ ソースを作成すると、表形式エディター (Model.bim) は読み取り専用になります。 表形式エディターを閉じ、ソリューション エクスプローラーから開き直すだけで、この問題を回避できます。

詳細な変更一覧については、[変更ログ](changelog-for-sql-server-data-tools-ssdt.md)を参照してください。

 > Visual Studio 2017 で SQL Server Data Tools を使用するには、後述する[こちら](#use-ssdt-in-visual-studio-2017)のセクションを参照してください。

  **使用できる言語**  
  
 SSDT の今回のリリースは、次の言語でインストールできます。  
[中国語 (中華人民共和国)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x804) | 
[中国語 (台湾)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x404) | 
[英語 (米国)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x409) | 
[フランス語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x40c)  
[ドイツ語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x407) | 
[イタリア語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x410) | 
[日本語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x411) | 
[韓国語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x412) | 
[ポルトガル語 (ブラジル)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x416) | 
[ロシア語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x419) | 
[スペイン語]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x40a)  

**ISO イメージ**

SSDT のインストールまたは管理者用インストール ポイントのセットアップの代替方法として、SSDT の ISO イメージを使用できます。 この ISO イメージは、SSDT に必要なすべてのコンポーネントが含まれた自己完結型ファイルであり、ダウンロード マネージャーを使用してダウンロードできます。ダウンロード マネージャーは再開可能であるため、ネットワークの帯域幅が限られている場合や信頼性が低い場合に便利です。 ダウンロードが完了したら、ISO イメージはドライブとしてマウントすることも、DVD に書き込むこともできます。

[中国語 (中華人民共和国)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x804) |
[中国語 (台湾)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x404) |
[英語 (米国)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x409) |
[フランス語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x40c)  
[ドイツ語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x407) |
[イタリア語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x410) |
[日本語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x411) |
[韓国語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x412) |
[ポルトガル語 (ブラジル)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x416) |
[ロシア語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x419) |
[スペイン語]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x40a)

<a id="download-visual-studio" class="xliff"></a>

## Visual Studio のダウンロード

* [**Visual Studio Community 2015 のダウンロード**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

<a id="installing-ssdt-without-visual-studio-pre-installed" class="xliff"></a>

## Visual Studio の事前インストールがない状態での SSDT のインストール

コンピューターに Visual Studio 2015 がインストールされていない場合、SSDT for Visual Studio 2015 をインストールすると、最小バージョン ("統合シェル") の Visual Studio 2015 もインストールされます。 このバージョンの Visual Studio は無料でインストールでき、必要な数のコンピューターで使用できます。 すべての種類の SQL Server プロジェクトに加え、SQL Server オブジェクト エクスプローラーおよび他の SQL ツールを使用できます。

コンピューターに [Visual Studio 2015 Community Edition (以降)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) がインストールされていない場合、SSDT をインストールすると、既存の Visual Studio に完全な SQL Server ツール セットが追加されます。 Visual Studio には、ソース コード管理の統合および非 SQL 言語のサポートなど、使用可能な多くの機能が含まれています。 T-SQL の開発時に快適に操作できるように、Visual Studio 2015 Community 以降を使用することをお勧めす。

<a id="supported-sql-versions" class="xliff"></a>

## サポートされる SQL のバージョン
  
|プロジェクト テンプレート|サポートされている SQL プラットフォーム|  
|-------------------|--------------------|  
リレーショナル データベース|  SQL Server 2005* - SQL Server 2017 <br /><br />Azure SQL データベース<br /><br />Azure SQL Data Warehouse (クエリのみサポートします。データベース プロジェクトはまだサポートされていません)<br /><br />  * SQL Server 2005 のサポートは推奨されていません。<br /><br /> 正式にサポートされている SQL バージョンに移行してください。|
  |Analysis Services モデル<br /><br />Reporting Services レポート | SQL Server 2008 – SQL Server 2017|
  |Integration Services パッケージ| SQL Server 2012 – SQL Server 2017    |
  
<a id="next-steps" class="xliff"></a>

## 次の手順  
SSDT をインストールした後、次のチュートリアルを使用して、SSDT を使ったデータベース、パッケージ、データ モデル、およびレポートの作成方法を学ぶことができます。  
  
-   [プロジェクト指向のオフライン データベース開発](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [SSIS チュートリアル: 簡単な ETL パッケージの作成](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Analysis Services チュートリアル](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [基本的なテーブル レポートの作成 (SSRS チュートリアル)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
<a id="use-ssdt-in-visual-studio-2017" class="xliff"></a>

## Visual Studio 2017 で SSDT を使用する 

* [**Visual Studio 2017 のダウンロード**](https://www.visualstudio.com/) ([Visual Studio 2017 のエディション別の機能の比較](https://www.visualstudio.com/vs/compare/))

リレーショナル データベース プロジェクトを使用するには、インストール中に**データの格納および処理**ワークロードをオンにすることをお勧めします。 SSDT データベース プロジェクトのサポートは、数多くの他のワークロードなどにも含まれています (*Azure*、"*ASP.Net と Web 開発*"、"*.Net Core クロス プラットフォーム開発*" など)。

> [!NOTE]
> 現在、Visual Studio 2017 の SSDT データベース プロジェクトは SQL Server 2016 までをサポートしています。  SQL Server 2017 は、Visual Studio 2017 の更新プログラムでまもなくサポートされます。

Visual Studio 2017 で SSDT を使用する場合は、AS コンポーネントと RS コンポーネントをインストールします。
* [Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)
* [Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


<a id="see-also" class="xliff"></a>

## 参照  
[Visual Studio の SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[SSDT MSDN フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT チーム ブログ](http://blogs.msdn.com/b/ssdt/)  
[SSDT Connect フィードバック](https://connect.microsoft.com/SQLServer/Feedback)  
[SSDT のドキュメント](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[DACFx API リファレンス](https://msdn.microsoft.com/library/dn645454.aspx)  
[SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  

