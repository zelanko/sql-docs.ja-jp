---
title: Analytics Platform System での高可用性 |Microsoft Docs
description: 高可用性の Analytics Platform System (APS) を構築する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cdf1837bd3b3b1cdf8e189ae591cd6fbff58387a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960865"
---
# <a name="analytics-platform-system-high-availability"></a>Analytics Platform System の高可用性
高可用性の Analytics Platform System (APS) を構築する方法について説明します。  
  
## <a name="high-availability-architecture"></a>高可用性のアーキテクチャ  
![アプライアンス アーキテクチャ](media/appliance-architecture.png "アプライアンスのアーキテクチャ")  
  
## <a name="network"></a>ネットワーク  
ネットワークの可用性、APS アプライアンスは、2 つの InfiniBand ネットワークを持っています。 いずれかの InfiniBand ネットワークがダウンした場合、もう 1 つは引き続き使用できます。 また、Active Directory が正しい InfiniBand ネットワークに着信要求を解決するのには、ドメイン コント ローラーをレプリケートします。  
  
詳細については、次を参照してください。[構成の InfiniBand ネットワーク アダプター](configure-infiniband-network-adapters.md)します。  
  
## <a name="storage"></a>ストレージ  
データを安全にするには、AP は RAID 1 ミラーリングのすべてのユーザー データの 2 つのコピーを維持するために使用します。 ディスクが失敗した場合、ハードウェア、システムはスペア ディスク上にデータを再構築し、ディスク障害が発生するアラートを設定します。  
  
使用可能なデータをオンライン保持するには、は、AP は、直接アタッチされたストレージでのユーザーのデータ ディスクを管理するのに Windows 記憶域スペースとクラスター化共有ボリュームを使用します。 マウント ポイントを介してコンピューティング ノードのホストに使用可能なクラスター共有ボリュームに編成されたデータのスケール ユニットごとに 1 つの記憶域プールがあります。  
  
記憶域プールはオンラインのままになることを確認するには、データのスケール ユニット内の各ホストに、ISCSI 仮想マシンはフェールオーバーされません。 データがデータのスケール ユニット内の他のホスト経由でアクセスできますが、ホストが失敗した場合、このアーキテクチャは重要です。  
  
## <a name="hosts"></a>Hosts  
ホストの可用性のすべてのホストには、Windows フェールオーバー クラスターに構成されます。 各ラックには、パッシブのホストがあります。 必要に応じて、SQL Server 並列データ ウェアハウス (PDW) およびアプライアンス ファブリックを制御するには、最初のラックには、2 つ目のパッシブ ホストことができます。 ホストが失敗した場合、使用可能なパッシブ ホストへのフェールオーバーで構成されている仮想マシンは経由で失敗します。  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>ノードの PDW およびアプライアンス ファブリック  
PDW ノードおよびアプライアンス ファブリックの高可用性は、AP は、仮想化を使用します。 PDW およびアプライアンス ファブリック コンポーネントのそれぞれは、仮想マシンで実行します。  
  
各仮想マシンは、Windows フェールオーバー クラスター内のロールとして定義されます。 仮想マシンが失敗すると、クラスターが、使用可能なパッシブ ホストで再起動します。 System Center Virtual Machine Manager を使用して仮想マシンがデプロイされます。 フェールオーバーが発生したときに、パッシブのホストで実行されている仮想マシンは InfiniBand ネットワークを介して、ユーザー データにアクセスすることができます。  
  
コントロールのノードとコンピューティング ノードの仮想マシンはそれぞれ単一ノード クラスターとして構成します。 単一ノード クラスターは、クラスターは、active の InfiniBand IP を使用して常に確認をクラスター リソースとしての InfiniBand ネットワークを管理します。 単一ノード クラスターでは、仮想マシン内で実行される PDW プロセスを管理します。 たとえば、単一ノード クラスターには、SQL Server とデータ移動サービス (DMS) リソースとしてに適切な順序で開始できるようにします。 制御ノード VM は、オーケストレーション ホスト上で実行される他の Vm の起動順序も制御します。  
  
