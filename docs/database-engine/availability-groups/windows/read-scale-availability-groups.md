---
title: "読み取りスケール可用性グループ | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6dfa046a07b9fd5a3eddbe474b5ea63c1163c26c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="read-scale-availability-groups"></a>読み取りスケール可用性グループ
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

SQL Server にそのクラスで最高の HA 機能をもたらすだけでなく、可用性グループは、統合スケーリング ソリューションも提供する包括的なソリューションです。 一般的なデータベース アプリケーションでは、複数のクライアントによりさまざまな種類のワークロードが実行され、その結果、リソース制約に起因し、ボトルネックを招くことがあります。 リソースを解放し、OLTP ワークロードのために高いスループットを達成し (高いパフォーマンスを届け)、読み取りのみのワークロードでスケーリングできます。 これは SQL Server の高速レプリケーション技術を活用することで達成できます。複製されたデータベースのグループを作成し、レポートと分析のワークロードを読み取り専用レプリカに移します。 

可用性グループを利用することで、セカンダリ データベースに読み取り専用アクセスできるように 1 つまたは複数のセカンダリ レプリカを構成できます。

レポートや分析のワークロードを実行するクライアント アプリケーションは、セカンダリ データベースに直接接続できます。 あるいは、顧客が読み取り専用ルーティング リストを作り、プライマリに接続できます。プライマリは、ルーティング リストに基づき、ラウンド ロビン方式で各セカンダリ レプリカに接続要求を転送します。

## <a name="read-scale-availability-groups-without-cluster"></a>読み取りスケール可用性グループ (クラスターなし)

[!INCLUDE[sssql15-md](..\..\..\includes\sssql15-md.md)] 以前では、すべての可用性グループにクラスターが必要でした。 そのクラスターにより、事業継続性、つまり、高可用性とディザスター リカバリー (HADR) が与えられました。 また、セカンダリ レプリカを読み取り操作に構成できました。 HA が目標でなかった場合、クラスターの構成と運用は多額の運用経費を意味しました。 SQL Server 2017 では、クラスターのない、読み取りスケール可用性グループが導入されました。 

プライマリで実行されるミッションクリティカルなワークロードのためにリソースを取っておく必要がある場合、読み取り専用のルーティングを利用するか、読み取り可能セカンダリ レプリカに直接接続できるようになりました。クラスタリング技術との統合に頼る必要がありません。 この新しい技術は、Windows プラットフォームと Linux プラットフォームの両方を実行している SQL Server 2017 で利用できます。

>[!IMPORTANT]
>これは高可用性設定ではありません。 障害検出と自動フェールオーバーを監視し、調整するためのインフラストラクチャはありません。 HADR 機能が必要な場合、クラスター マネージャー (Windows の WSFC または Linux の Pacemaker) を利用してください。 

## <a name="use-distributed-availability-groups-for-geographic-read-scale"></a>地理的読み取りスケールに分散型可用性グループを使用する

地理的に離れたソリューションでは、読み取りスケール ソリューションと分散型可用性グループを実装できます。 プライマリ レプリカから読み取り可能セカンダリ レプリカに読み取り負荷を移し、読み取りワークロードの発生源に近いサイトに負荷を移します。 プライマリのリソースの利用率を減らすだけでなく、ネットワーク待機時間を減らし、専用リソースを活用することで読み取りスループットを増やします。

1 個の分散型可用性グループで最大 17 個のセカンダリ レプリカを持つことができます。 スケーリング容量が増えた場合、複数の可用性グループをデイジー チェーン接続し、読み取り可能レプリカの数をさらに増やすことができます。 同じ可用性グループから 2 つの分散型可用性グループを展開すれば、地理的に分散した環境で読み取りの待機時間を減らすことができます。




## <a name="next-steps"></a>次の手順 

[Linux で読み取りスケール可用性グループを構成する](../../../linux/sql-server-linux-availability-group-configure-rs.md)

## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

