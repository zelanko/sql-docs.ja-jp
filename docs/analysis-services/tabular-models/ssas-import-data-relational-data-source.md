---
title: "リレーショナル データ ソース (SSAS テーブル) からのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1db6dd24d059f8c478967bc3c69652aaec0aeb51
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---relational-data-source"></a>データのインポート、リレーショナル データ ソース
  テーブルのインポート ウィザードを使用して、さまざまなリレーショナル データベースからデータをインポートできます。 このウィザードは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **[モデル]** メニューで使用できます。 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。 サポートされているデータ ソースおよびプロバイダーの詳細については、「 [サポートされているデータ ソース (SSAS テーブル)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。  
  
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
  
 テーブルのインポート ウィザードでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをデータ ソースとするデータのインポートはサポートされません。  
  
### <a name="to-import-data-from-a-database"></a>データベースからのデータをインポートするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]**をクリックします。  
  
2.  **[データ ソースへの接続]** ページで接続するデータベースの種類を選択し、 **[次へ]**をクリックします。  
  
3.  テーブルのインポート ウィザードの手順に従って操作します。 後続のページでは、 **[テーブルとビューの選択]** ページを使用するか、または **[SQL クエリの指定]** ページで SQL クエリを作成することにより、特定のテーブルおよびビューの選択や、フィルターの適用を行うことができます。  
  
## <a name="see-also"></a>参照  
 [データのインポート (SSAS テーブル)](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [サポートされているデータ ソース (SSAS テーブル)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
