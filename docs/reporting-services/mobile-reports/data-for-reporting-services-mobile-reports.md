---
title: "Reporting Services モバイル レポートのデータを |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
caps.latest.revision: 15
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 9cf879fae78095f5fa6cb6f10d20cb0dfe6d12a1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="data-for-reporting-services-mobile-reports"></a>Reporting Services モバイル レポートのデータ
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] のデータ モデルは単純です。 データは、データセットのコレクションとして [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] にインポートされます。 データセット間の正式なリレーションシップは必要ありません。 あるデータセットから別のデータセットの参照は、キーの値が一致する限り機能します。 日付/時刻の集計は、モバイル レポート ランタイムによって処理されます。日付/時刻データの細分性がデータセットの間で異なる場合でも、この集計は異なるデータセットの間で一致します。   
  
2 つの種類のソースからデータをインポートできます。   
  
* **ローカルの Excel ファイル**: Excel のドキュメントを選択し、インポートするワークシートを選択します。 インポート後に、データはモバイル レポート定義内に保存されます。 元の Excel ファイルからのデータを更新するには、 **の** [データ] [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **Data** tab.詳細について[SSRS モバイル レポートを Excel のデータを準備する](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)です。  
  
* **[!INCLUDE[PRODUCT_NAME](../../includes/server-product-name.md)] 共有データセット**: サーバー上のパブリッシュされたデータセットの一覧を参照し、モバイル レポートに追加するデータセットを選択します。 サーバー データに基づくモバイル レポートは、常に元のサーバーのデータセットに接続され、サーバー上のデータの最新の状態が反映されます。 「 [サポートされるデータ ソースの一覧](https://msdn.microsoft.com/library/ms159219.aspx)」を参照してください。   
  
  詳細については、 [Mobile Report Publisher での共有データセットからのデータの取得](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)に関する記事を参照してください。  
  
データを [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]にインポートした後は、データの入手先にかかわらず、残りのモバイル レポートの作成とデザイン環境は同じになります。   
  
## <a name="connect-mobile-report-elements-to-data"></a>モバイル レポート要素とデータの接続 ##  
  
各 [!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] 要素には、1 つ以上のデータ設定が含まれています。 たとえば、放射状ゲージの要素には 2 つのデータ設定が含まれます。メイン値と比較対象値です。 これらの各設定は、特定のデータセット内の 1 つのフィールド (列) を正確にポイントします。   
  
モバイル レポート ランタイムでは、ユーザーの選択に基づいて、ゲージの集計値を提供します。 同じ放射状ゲージ インスタンスの比較対象値は、異なるデータセットのフィールドにバインドされることがあります。   
  
### <a name="see-also"></a>参照  
-  [Reporting Services モバイル レポート用にデータを準備する](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [共有データセットからデータを取得する](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [モバイル レポートで Analysis Services データの日付の書式設定を保持する](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  


