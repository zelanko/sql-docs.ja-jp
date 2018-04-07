---
title: Analytics Platform System の高可用性
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: 高可用性の Analytics Platform System (APS) を構築する方法について説明します。
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 5ab245e9-0316-4d25-a626-4745ce856925
caps.latest.revision: 9
ms.openlocfilehash: 9fd057a4cd673f06034e0093ca93be7ceaf345ea
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="analytics-platform-system-high-availability"></a>Analytics Platform System の高可用性
高可用性の Analytics Platform System (APS) を構築する方法について説明します。  
  
## <a name="high-availability-architecture"></a>高可用性アーキテクチャ  
![アプライアンス アーキテクチャ](media/appliance-architecture.png "アプライアンス アーキテクチャ")  
  
## <a name="network"></a>ネットワーク  
ネットワークの可用性、AP アプライアンスは、2 つの InfiniBand ネットワークを持っています。 いずれかの InfiniBand ネットワークがダウンした場合、もう一方が引き続き使用できます。 また、Active Directory が正しい InfiniBand ネットワークに着信要求を解決するのにはドメイン コント ローラーをレプリケートします。  
  
詳細については、次を参照してください。[構成の InfiniBand ネットワーク アダプター](configure-infiniband-network-adapters.md)です。  
  
## <a name="storage"></a>ストレージ  
データを安全に保つには、APS は RAID 1 ミラーリングのすべてのユーザー データの 2 つのコピーを維持するために使用します。 ディスクが失敗すると、ハードウェア システムは予備のディスク上にデータを再構築し、ディスク障害があること、アラートを設定します。  
  
データを保持する使用可能なオンライン、AP は、直接アタッチされたストレージ内のユーザー データ ディスクを管理するのに Windows 記憶域スペースとクラスター化共有ボリュームを使用します。 コンピューティング ノードのホストにマウント ポイントを介して使用可能なクラスター共有ボリュームに編成データのスケール単位あたり 1 つの記憶域プールがあります。  
  
記憶域プールはオンラインのままになることを確認するには、データのスケール ユニット内の各ホストに、ISCSI 仮想マシンをフェールオーバーできません。 このアーキテクチャは、データが、データのスケール ユニットに他のホスト経由でアクセスできますが、ホストが失敗した場合、重要です。  
  
## <a name="hosts"></a>Hosts  
ホストの可用性、すべてのホストには、Windows フェールオーバー クラスターに構成されます。 各ラックには、パッシブのホストがあります。 必要に応じて SQL Server 並列データ ウェアハウス (PDW) とアプライアンス ファブリックを制御するには、最初のラックには、2 番目のパッシブ ホストことができます。 ホストが失敗した場合、フェールオーバーは、構成されている仮想マシンはフェールオーバーに利用可能なパッシブ ホストします。  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>PDW ノードとアプライアンス ファブリック  
PDW ノードとアプライアンス fabric の高可用性は、AP は、仮想化を使用します。 各 PDW アプライアンスとファブリック コンポーネントは、仮想マシンで実行します。  
  
各仮想マシンは、Windows フェールオーバー クラスターの役割として定義されます。 仮想マシンが失敗すると、クラスターは、可用性パッシブ ホスト上に再起動します。 System Center Virtual Machine Manager を使用して仮想マシンが展開されます。 フェールオーバーが発生したときに、パッシブ ホストで実行されている仮想マシンは InfiniBand ネットワーク経由のユーザー データにアクセスできないです。  
  
コントロールのノードとコンピューティング ノードの仮想マシンはそれぞれ単一ノード クラスターとして構成します。 単一ノード クラスターでは、クラスターは、active の InfiniBand IP を使用して常に確認をクラスター リソースとして InfiniBand ネットワークを管理します。 単一ノード クラスターでは、仮想マシン内で実行されている PDW プロセスを管理します。 たとえば、単一ノード クラスターには、SQL Server とのデータ移動サービス (DM) リソースとしてに適切な順序で開始できるようにします。 コントロールのノード VM は、オーケストレーション ホスト上で実行される他の Vm の起動順序も制御します。  
  
