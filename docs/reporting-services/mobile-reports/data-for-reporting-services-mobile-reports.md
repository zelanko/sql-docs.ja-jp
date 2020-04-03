---
title: Reporting Services モバイル レポートのデータ | Microsoft Docs
description: SQL Server Mobile Report Publisher にデータをインポートした後、データが Excel ファイルか共有データセットのどちらであるかにかかわらず、モバイル レポートの作成とデザインは同じになります。
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3c022631d0f21c4e23756e39e4824fe9f52ef3b5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79447860"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Reporting Services モバイル レポートのデータ
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] のデータ モデルは単純です。 データは、データセットのコレクションとして [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] にインポートされます。 データセット間の正式なリレーションシップは必要ありません。 あるデータセットから別のデータセットの参照は、キーの値が一致する限り機能します。 日付/時刻の集計は、モバイル レポート ランタイムによって処理されます。日付/時刻データの細分性がデータセットの間で異なる場合でも、この集計は異なるデータセットの間で一致します。   
  
2 つの種類のソースからデータをインポートできます。   
  
* **ローカルの Excel ファイル**:Excel のドキュメントを選択し、インポートするワークシートを選択します。 インポート後に、データはモバイル レポート定義内に保存されます。 元の Excel ファイルのデータを更新するには、[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] **[データ]** タブの右上隅の **[データの更新]** コマンドを使用します。詳細については、[SSRS モバイル レポート用の Excel データの準備](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)に関するページを参照してください。  
  
* **SQL Server Mobile Report Publisher 共有データセット**:サーバー上のパブリッシュされたデータセットの一覧を参照し、モバイル レポートに追加するデータセットを選択します。 サーバー データに基づくモバイル レポートは、常に元のサーバーのデータセットに接続され、サーバー上のデータの最新の状態が反映されます。 [サポートされるデータ ソースの一覧](../report-data/data-sources-supported-by-reporting-services-ssrs.md)に関するページを参照してください。   
  
  詳細については、 [Mobile Report Publisher での共有データセットからのデータの取得](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)に関する記事を参照してください。  
  
データを [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]にインポートした後は、データの入手先にかかわらず、残りのモバイル レポートの作成とデザイン環境は同じになります。   
  
## <a name="connect-mobile-report-elements-to-data"></a>モバイル レポート要素とデータの接続 ##  
  
SQL Server Mobile Report Publisher の各要素には、1 つ以上のデータ設定が含まれています。 たとえば、放射状ゲージの要素には 2 つのデータ設定が含まれます。[主要な値] と [比較対象値] です。 これらの各設定は、特定のデータセット内の 1 つのフィールド (列) を正確にポイントします。   
  
モバイル レポート ランタイムでは、ユーザーの選択に基づいて、ゲージの集計値を提供します。 同じ放射状ゲージ インスタンスの比較対象値は、異なるデータセットのフィールドにバインドされることがあります。   
  
### <a name="see-also"></a>関連項目  
-  [Reporting Services モバイル レポート用にデータを準備する](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [共有データセットからデータを取得する](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [モバイル レポートで Analysis Services データの日付の書式設定を保持する](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

