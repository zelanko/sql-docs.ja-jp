---
title: "概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 01/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d4dcb00-b93e-44db-9d67-061702bba41a
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e5a3dd9c765c347b7516706d6e157a47f3c9bd03
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="wide-world-importers-overview"></a>Wide World Importers 社の概要
これは、架空の会社の Wide World importers 社と SQL Server と Azure SQL Database の WideWorldImporters サンプル データベースに送られるワークフローの概要です。  

Wide World Importers 社 (WWI) は、卸売り新奇商品インポーターと San Francisco ベイ領域から運用ディストリビューターです。

WWI の顧客、卸売り業個人に再販する企業ほとんどの場合があります。 WWI 顧客に販売小売全米スーパー マーケット、specialty ストアを含むストア、観光引力店、および一部のユーザーを計算します。 また、WWI は WWI の代理で製品を推進しているエージェントのネットワークを経由して他の wholesalers を販売しています。 現在、米国の州基づいて WWI の顧客のすべてが、他の国に拡張するためにプッシュするは、会社は必ずしも意図しています。

WWI 新奇と toy 製造元、および他の新奇 wholesalers サプライヤーから商品を購入します。 顧客の注文を受け付けますに必要な在庫、WWI ウェアハウスと仕入先からの発注で商品をします。 これらも資料、パッケージの大容量のボリュームを購入しより小さい数量でこれらをお客様の便宜を図って販売します。

最近 WWI 活用 novelties chilli などのさまざまなチョコレートを販売するために開始しました。  会社は以前、chilled 項目を処理する必要はありません。 ここで、食品の処理の要件を満たすためには、その chiller ルームとを持つ chiller のセクションでは、車のいずれかで温度必要があります監視します。

## <a name="workflow-for-warehouse-stock-items"></a>ウェアハウス品目の在庫のワークフロー

品目を在庫し、分散する方法の一般的なフローは次のとおりです。
- WWI は発注書を作成し、仕入先に送信します。
- アイテムを業者に送信、WWI が受信して、倉庫で在庫にします。
- WWI から顧客注文項目
- WWI がウェアハウスでは、株価の項目を含む顧客の注文を入力し、仕入先から追加の在庫を注文するための十分な在庫があるないと、します。
- 一部のお客様は、在庫がない項目まで待つしないようにします。 5 つの異なる注文と品目を在庫と 4 つが利用可能なの 4 つの項目と受注残残りの項目を受信します。 項目別の出荷の後で送信されることです。
- WWI 請求書の品目を在庫に顧客の通常の順序を請求書に変換することによってです。
- お客様は、在庫がない項目を順序可能性があります。 これらのアイテムはバック オーダーが存在します。
- WWI は、品目の在庫を独自の配信 van 経由で、または他のクーリエまたは freight メソッドを通じて顧客に提供します。
- 顧客は、WWI に請求書を支払います。
- 定期的に、WWI は発注書になった項目のサプライヤーを支払います。 これは多くの場合、しばらく商品を受信した後です。

## <a name="data-warehouse-and-analysis-workflow"></a>データ ウェアハウスと分析のワークフロー

WWI のチームは、WideWorldImporters データベースから運用レポートを生成する SQL Server Reporting Services を使用して、それらをデータ分析を実行し、戦略的なレポートを生成する必要がある必要があります。 チームは、データベース WideWorldImportersDW の次元のデータ モデルを作成しました。 このデータベースは、Integration Services パッケージによって設定されます。

SQL Server Analysis Services を使用して、ディメンション データ モデル内のデータから分析データ モデルを作成します。 SQL Server Reporting Services を使用して、ディメンション データ モデルから直接と同様に、分析のモデルに戦略的なレポートを生成します。 Power BI を使用して、同じデータからダッシュ ボードを作成します。 ダッシュ ボードは、web サイト、および携帯電話とタブレットに使用されます。 *注: これらデータ モデルとレポートはまだ使用できません。*

## <a name="additional-workflows"></a>追加のワークフロー

これらは、追加のワークフローです。
- WWI 問題クレジット ノートときに、顧客、何らかの理由や、商品が障害のある、good を受信しません。 これらは、請求書の負の値として扱われます。
- WWI は手の形での表示、システムで利用可能な在庫数量が正確であることを確認する品目の在庫量を定期的にカウントします。 (これを行うプロセスが呼び出されます、stocktake)。
- コールド ルーム温度。 生鮮商品は冷蔵ルームに格納されます。 これらのルームのセンサー データは、データベースの監視と分析のために取り込まれです。
- 車の場所を追跡します。 商品のトランスポートに WWI 車両には、場所を追跡するセンサーが含まれます。 この場所は再び監視し、さらに分析用にデータベースに取り込まれです。

## <a name="fiscal-year"></a>会計年度

会社は、年 11 月 1 日に開始される会計年度で動作します。

## <a name="terms-of-use"></a>使用条件

ここに記載されて、サンプル データベースとサンプル コードのライセンス: [license.txt](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

サンプル データベースには、data.gov と自然 EarthData から読み込まれている公開データが含まれています。 使用条件がここでは: [http://www.naturalearthdata.com/about/terms-of-use/](http://www.naturalearthdata.com/about/terms-of-use/)

