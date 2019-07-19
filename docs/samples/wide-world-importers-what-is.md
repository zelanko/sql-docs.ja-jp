---
title: Wide World Importers - SQL のサンプル データベース |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c178d116dddb5dc18b1bec91066205fe08f6d0c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067609"
---
# <a name="wide-world-importers-sample-databases-for-microsoft-sql"></a>Microsoft SQL の wide World Importers のサンプル データベース
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
これは、架空の会社の Wide World importers 社と SQL Server と Azure SQL Database の WideWorldImporters サンプル データベースに送られるワークフローの概要です。  

Wide World importers 社 (WWI) とは、卸売り新奇商品インポーターと San Francisco ベイ領域から運用をディストリビューターです。

WWI の顧客、卸売業者の個人に再販企業ほとんどの場合があります。 WWI 顧客に販売小売などの専門的なストアでは、スーパー マーケットでは、米国ストア、観光引き寄せる力ショップ、および一部のユーザーを計算します。 WWI も、WWI の代わりに製品を推進しているエージェントのネットワーク経由で他の卸売を販売しています。 米国の州ベース WWI の顧客のすべての現在は、会社がその他の国に拡張するためにプッシュしようとします。

WWI など新奇と玩具メーカー、およびその他の新奇卸売業者からの商品を購入します。 WWI ウェアハウスし、サプライヤーから並べ替え商品は、顧客の注文を満たすために必要に応じて、ストックします。 膨大な量の資料、パッケージ化の購入や利便性のため、顧客を販売するこれら小さい数にもします。

最近 WWI は、活用 novelties chilli などのさまざまなチョコレートの販売を開始しました。  会社以前がありませんでした chilled 項目を処理します。 ここで、食品の処理の要件を満たすためには、その冷却装置ルームおよびを持つ chiller のセクションでは、トラックのいずれかで温度を監視する必要があります。

## <a name="workflow-for-warehouse-stock-items"></a>倉庫の品目の在庫のワークフロー

品目の在庫し、分散の方法の一般的なフローは次のとおりです。
- WWI は発注書を作成し、仕入先に送信します。
- アイテムをサプライヤーに送信、WWI がそれらを受け取るし、倉庫の在庫にします。
- WWI 顧客注文項目
- WWI がウェアハウスの株式の項目を含む顧客の注文を入力し、仕入先から追加の在庫を注文するための十分な在庫がいないときにします。
- 一部のお客様は、在庫がない項目を待機しません。 5 つの異なる注文と品目を在庫と 4 が利用可能な 4 つの項目と受注残残りの項目を受信します。 アイテムに個別の出荷で後で送信されるとします。
- WWI 請求書に順序を変換することによって通常品目を在庫の顧客を請求します。
- 在庫がないアイテムを注文する場合があります。 これらのアイテムは、取り寄せ注文中です。
- WWI 品目の在庫を独自の配信 van またはその他のクーリエまたは運賃メソッドを使用して顧客に配信します。
- お客様は、WWI に請求書をお支払い。
- 定期的に、WWI は、注文書の品目のサプライヤーを支払います。 これは多くの場合、いずれかの時点、商品を受信した後です。

## <a name="data-warehouse-and-analysis-workflow"></a>データ ウェアハウスと分析のワークフロー

WWI のチームでは、WideWorldImporters データベースから運用レポートを生成する SQL Server Reporting Services を使用して、それらのデータを分析を行い、戦略的なレポートを生成する必要がある必要があります。 チームは、データベース WideWorldImportersDW の次元のデータ モデルを作成しました。 このデータベースは、Integration Services パッケージによって設定されます。

SQL Server Analysis Services を使用して、次元のデータ モデル内のデータから分析データ モデルを作成します。 SQL Server Reporting Services は、次元のデータ モデルから直接、分析、モデルからも、戦略的なレポートを生成するために使用します。 Power BI を使用して、同じデータからダッシュ ボードを作成します。 ダッシュ ボードは、web サイト、および携帯電話とタブレットで使用されます。 *注: これらのデータ モデルとレポートはまだ使用可能です*

## <a name="additional-workflows"></a>追加のワークフロー

これらは、追加のワークフローです。
- WWI 問題貸方票ときに、顧客は、何らかの理由で、または商品が障害のある、good を受信しません。 これらは、請求書が負の値として扱われます。
- WWI は定期的に在庫の数量がシステムに利用可能な表示が正確であることを確認する品目の在庫の手持ち数量をカウントします。 (これを行うプロセスが呼び出されます、stocktake)。
- コールド部屋の温度。 Perishable 商品は、冷蔵ルームに格納されます。 これらの部屋からのセンサー データは、データベースの監視と分析のために取り込まれます。
- 車両の場所の追跡。 WWI の商品を配送車両には、場所を追跡するセンサーが含まれます。 この場所は、もう一度の監視と分析をさらに、データベースに取り込まれます。

## <a name="fiscal-year"></a>会計年度

会社は、11 月 1 日に開始される事業年度で動作します。

## <a name="terms-of-use"></a>使用条件

ここで、サンプル データベースとサンプル コードのライセンスは説明: [license.txt](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

サンプル データベースには、data.gov と自然 EarthData から読み込まれているパブリック データが含まれています。 使用条件は、ここでは。 [https://www.naturalearthdata.com/about/terms-of-use/](https://www.naturalearthdata.com/about/terms-of-use/)
