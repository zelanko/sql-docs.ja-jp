---
title: ワイド World importers 社 - SQL のサンプル データベース |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5a1eef0650c520ff4757de627633d096ffa46ec8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33032649"
---
# <a name="wide-world-importers-sample-databases-for-microsoft-sql"></a>Wide World Importers のサンプルの Microsoft SQL データベース
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
これは、架空の会社の Wide World importers 社と SQL Server と Azure SQL Database の WideWorldImporters サンプル データベースに送られるワークフローの概要です。  

Wide World Importers (WWI) は、サンフランシスコ ベイエリアで活動している、ノベルティ商品の卸売りのインポーターおよびディストリビューターです。

WWI は卸売業者のため、その顧客は個人に対して再販する企業がほとんどです。WWI は、専門店、スーパー マーケット、コンピューター販売店、観光関連のお店および個人を含む米国全土の小売客に販売します。また、WWI は WWI の代理で製品を推進しているエージェントのネットワークを経由して他の卸売業者に販売しています。現時点では WWI の顧客のすべてが米国を拠点としていますが、WWI は他国への進出も計画しています。

WWI は、ノベルティや玩具の製造元、および他のノベルティ卸売業者を含むサプライヤーから商品を購入します。WWI は WWI ウェアハウスに商品をストックし、顧客の注文に応じて、サプライヤーから再度発注します。また、WWI は大量の梱包材を購入し、顧客の必要に合わせて少量を販売します。

最近 WWI は、チリ チョコレートなどの食用ノベルティの販売を開始しました。これまで WWI は、冷蔵アイテムを管理する必要はありませんでした。現在は、食品の管理要件を満たすために、冷蔵室、および冷蔵セクションがあるトラックの温度を監視する必要があります。

## <a name="workflow-for-warehouse-stock-items"></a>ウェアハウス品目の在庫のワークフロー

品目を在庫し、分散する方法の一般的なフローは次のとおりです。
- WWI は発注書を作成し、仕入先に送信します。
- 仕入れ先がアイテムを送り、WWI が受け取って倉庫に保管します。
- 顧客が WWI からアイテムを注文します。
- WWI は倉庫内の在庫から顧客の注文に対応し、十分の在庫がない場合は、仕入先から追加注文します。
- 一部のお客様は、在庫がない項目まで待つしないようにします。 5 つの異なる注文と品目を在庫と 4 つが利用可能なの 4 つの項目と受注残残りの項目を受信します。 項目別の出荷の後で送信されることです。
- WWI は、一般的に注文を請求書に置き換えることによって、在庫に関して顧客に請求します。
- お客様は、在庫がない項目を順序可能性があります。 これらのアイテムはバック オーダーが存在します。
- WWI は、独自のトラックまたは他の配達業者や輸送方法のいずれかを通じて顧客に在庫品提供します。
- 顧客は、WWI に請求書に対する支払いをします。
- WWI は定期的に発注書に記載された項目を仕入れ先に支払います。これは多くの場合、商品を受け取ってしばらく経った後に行われます。

## <a name="data-warehouse-and-analysis-workflow"></a>データ ウェアハウスと分析のワークフロー

WWI のチームは、SQL Server Reporting Services を使用して WideWorldImporters データベースから運用レポートを生成しますが、データ分析を実行し、戦略レポートを生成する必要もあります。 チームは、データベース WideWorldImportersDW にディメンション データ モデルを作成しました。このデータベースは、Integration Services パッケージによって設定されます。

SQL Server Analysis Services を使用して、ディメンション データ モデル内のデータから分析データ モデルを作成します。 SQL Server Reporting Services を使用して、ディメンション データ モデルから直接と同様に、分析のモデルに戦略的なレポートを生成します。 Power BI を使用して、同じデータからダッシュ ボードを作成します。 ダッシュ ボードは、web サイト、および携帯電話とタブレットに使用されます。 *注: これらデータ モデルとレポートはまだ使用できません。*

## <a name="additional-workflows"></a>追加のワークフロー

これらは、追加のワークフローです。
- WWI は、何らかの理由で商品が顧客に届かない場合や、商品に欠陥がある場合に訂正表を発行します。これらは、請求書の負の値として扱われます。
- WWI は在庫品の在庫数量を定期的にカウントし、システムに表示されている在庫数量が正確であることを確認します。(これを行うプロセスは、「棚卸」と呼ばれます)。
- コールド ルーム温度。 生鮮商品は冷蔵ルームに格納されます。 これらのルームのセンサー データは、データベースの監視と分析のために取り込まれです。
- 車両の場所を追跡します。商品の配送に使われる WWI の車両には、場所を追跡するセンサーが搭載されています。この場所は再度データベースに取り込まれ、監視および詳細な分析を行います。

## <a name="fiscal-year"></a>会計年度

会社は、年 11 月 1 日に開始される会計年度で動作します。

## <a name="terms-of-use"></a>使用条件

ここに記載されて、サンプル データベースとサンプル コードのライセンス: [license.txt](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

サンプル データベースには、data.gov と自然 EarthData から読み込まれている公開データが含まれています。 使用条件は、ここでは。 [http://www.naturalearthdata.com/about/terms-of-use/](http://www.naturalearthdata.com/about/terms-of-use/)
