---
title: Analysis services 表形式モデルの互換性レベル |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd70a673744d2e401e8a28f6ce2c533434e1c75e
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472311"
---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Analysis Services 表形式モデルの互換性レベル
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  *互換性レベル*Analysis Services エンジンにおけるリリースに固有の動作を参照します。 たとえば、DirectQuery と表形式オブジェクトのメタデータ、互換性レベルによってさまざまな実装があります。 一般に、サーバーでサポートされている最新の互換性レベルを選択してください。

  **最新の互換性レベルは、1400 です。** 
  
互換性レベル 1400 の主な機能は次のとおりです。

*  TOM Api と TMSL スクリプト対応のデータ接続と表形式モデルへのインポートの新しいインフラストラクチャ。 これにより、Azure Blob ストレージなどの追加のデータ ソースのサポート。 追加のデータ ソースは、今後の更新に含まれます。
*  データ変換と SSDT でデータの取得と M 式を使用して、データのマッシュ アップ機能。
*  メジャーの集計されたレポートから詳細なデータにドリル ダウンの Microsoft Excel などの BI ツールを有効にする、DAX 式で Detail Rows プロパティようになりました。 たとえば、エンドユーザーは、地域と月の売上合計を表示するときに、関連付けられている注文の詳細表示できます。 
*  オブジェクト レベルのセキュリティに含まれるデータに加え、テーブルと列の名前。
*  不規則階層のサポートの強化。
*  パフォーマンスと監視の機能強化。

  
## <a name="supported-compatibility-levels-by-version"></a>バージョンでサポートされる互換性レベル
  
|||  
|-|-|- 
|**互換性レベル**|**サーバーのバージョン**| 
|1400|Azure Analysis Services、SQL Server 2017 |  
|1200|Azure Analysis Services、SQL Server 2017 では、SQL Server 2016| 
|1103|SQL Server 2017 *、SQL Server 2016、SQL Server 2014、SQL Server 2012 SP1|  
|1100|SQL Server 2017 *、SQL Server 2016、SQL Server 2014、SQL Server 2012 SP1、SQL Server 2012| 

\* SQL Server 2017 では、1100 と 1103 互換性レベルが非推奨とされます。
  
## <a name="set-compatibility-level"></a>互換性レベルの設定 
 SQL Server Data Tools (SSDT) を新しいテーブル モデル プロジェクトを作成するときに、互換性レベルを指定できます、**表形式モデル デザイナー**ダイアログ。 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 選択した場合、**今後このメッセージを表示しない**オプション、後続のすべてのプロジェクトには、既定値として指定した互換性レベルが使用されます。 SSDT の既定の互換性レベルは、 **[ツール]** > **[オプション]** の順に選択すると変更できます。  
  
 SSDT で表形式モデル プロジェクトをアップグレードするには、設定、**互換性レベル**モデル内のプロパティ**プロパティ**ウィンドウ。 注意して、互換性レベルのアップグレードは元に戻すことはありません。
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>SSMS でデータベースの互換性レベルを確認する  
 SSMS でデータベース名を右クリックして >**プロパティ** > **互換性レベル**します。  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>SSMS でサーバーのサポートされる互換性レベルを確認する  
 SSMS で、サーバー名を右クリックして >**プロパティ** > **サポートされる互換性レベル**します。  
  
 このプロパティは、サーバーで実行されるデータベースの最も高い互換性レベルを指定します。 サポートされる互換性レベルは読み取り専用であり、変更できません。  
  
## <a name="see-also"></a>参照  
 [多次元データベースの互換性レベル](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [What's new in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [新しい表形式モデル プロジェクトを作成します。](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
