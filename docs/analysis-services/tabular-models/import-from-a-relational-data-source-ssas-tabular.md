---
title: "リレーショナル データ ソースからのインポート (SSAS テーブル) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# リレーショナル データ ソースからのインポート (SSAS テーブル)
  テーブルのインポート ウィザードを使用して、さまざまなリレーショナル データベースからデータをインポートできます。 このウィザードは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[モデル]** メニューで使用できます。 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。 サポートされているデータ ソースおよびプロバイダーの詳細については、「[サポートされているデータ ソース (SSAS テーブル)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。  
  
 テーブルのインポート ウィザードでは、次のデータ ソースからのデータのインポートがサポートされています。  
  
 **リレーショナル データベース**  
  
-   Microsoft SQL Server データベース  
  
-   Microsoft SQL Azure  
  
-   Microsoft Access データベース  
  
-   Microsoft SQL Server 並列データ ウェアハウス  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **多次元ソース**  
  
-   Microsoft SQL Server Analysis Services キューブ  
  
 テーブルのインポート ウィザードでは、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをデータ ソースとするデータのインポートはサポートされません。  
  
### データベースからのデータをインポートするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]**をクリックします。  
  
2.  **[データ ソースへの接続]** ページで接続するデータベースの種類を選択し、**[次へ]** をクリックします。  
  
3.  テーブルのインポート ウィザードの手順に従って操作します。 後続のページでは、**[テーブルとビューの選択]** ページを使用するか、または **[SQL クエリの指定]** ページで SQL クエリを作成することにより、特定のテーブルおよびビューの選択や、フィルターの適用を行うことができます。  
  
## 参照  
 [データのインポート (SSAS テーブル)](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [サポートされているデータ ソース (SSAS テーブル)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  