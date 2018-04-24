---
title: アプライアンスの物理的なコンポーネントの分析プラットフォーム システム |Microsoft ドキュメント
description: 名前と説明の PDW アプライアンスとファブリックの物理コンポーネント。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0adbd92d1a29a98a80de65268c53ea63e3941d07
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="appliance-physical-components---analytics-platform-system"></a>アプライアンスの物理的なコンポーネントの分析プラットフォーム システム
名前と説明の PDW アプライアンスとファブリックの物理コンポーネント。 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>コンポーネント図  
これは、物理的なコンポーネントと 6 コンピューティング ノード アプライアンスの最初のラックの場所の名前を示しています。  
  
![PDW リージョン コンポーネント名 - HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames HP")  
  
PDW コンポーネントの実際の名前は、ダッシュ、コンポーネント名を続けて、PDW 領域名前です。 たとえば、PDW 地域名が PDW123 の場合は、実際の名前は**PDW123 CTL01**、 **PDW123 CMP01**, などです。  
  
同様に、アプライアンス ファブリック コンポーネントの実際の名前は、ダッシュ、コンポーネント名を続けて、アプライアンス ドメインです。 たとえば、アプライアンスのドメインが FSW123 の場合は、アプライアンス ファブリック Vm は**FSW123 WDS**、 **FSW123 AD01**、 **FSW123 VMM**, などです。  
  
ここで、6 つの計算ノードを伴う PDW 領域の統合ビューです。  
  
![PDW コンポーネント名](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>PDW コンポーネント  
PDW の仮想マシンは、PDW 領域の一部です。  
  
*PDW_region*-CTL01  
コントロールのノードを実行する仮想マシン。 これにより、HST01 で実行し、HST02 にフェールオーバーすることができます。  
  
> [!WARNING]  
> SQL Server PDW は、HYPER-V マネージャーを使用して、CTL01 仮想マシンのスナップショットの作成をサポートしていません。 スナップショットは、仮想マシンのバックアップをフェールオーバーしようとすると、エラーが発生するローカル ストレージに依存します。 スナップショットを作成することができますも信頼性で問題が発生、他の VM のパッシブのサーバーにフェールオーバーします。  
  
*PDW_region*-を通じて CMP01 *PDW_Region*-CMP06  
コンピューティング ノードを実行する仮想マシン。 図ではこの 6 コンピューティング ノード、ホスト HSA01 実行 HSA06 をコンピューティング ノード Vm CMP01 CMP06 を通じてそれぞれします。  
  
## <a name="fabric"></a>アプライアンス ファブリック コンポーネント  
これらのコンポーネントは、アプライアンスのファブリックの一部です。  
  
### <a name="virtual-machines"></a>仮想マシン  
*appliance_domain*-WDS  
このバーチャル マシン ホスト Analytics Platform System を使用する Windows 展開サービス (WDS)、アプライアンス ネットワーク経由で Windows オペレーティング システムを展開します。 アプライアンス ホストの構成済みの IP アドレスをしなくてもアプライアンス ネットワークに参加できるようにする、DHCP サービスもホストします。  
  
*Appliance_domain*WDS-仮想マシンが HST01 上で実行し、HST02 にフェールオーバーすることができます。 WDS の仮想マシンと VMM バーチャル マシンは、アプライアンスのインストール中に、物理ホスト上に Windows を展開できます。 WDS と VMM は、アプライアンスのライフ サイクル中にホストを交換などの操作を実行します。  
  
*appliance_domain*VMM  
Virtual Machine Manager (VMM) は、仮想マシンで実行され、HST02 にフェールオーバーすることができます。 VMM では、物理ホスト上のオペレーティング システムを展開する System Center をホストします。 VMM では、適用またはすべてのホストとバーチャル マシン間での Windows 更新プログラムを削除する Windows Server Update Services (WSUS) も提供します。  
  
*appliance_domain*-AD01、 *appliance_domain*-AD02  
Active Directory ドメイン サービス ドメイン ネーム システム (DNS) が含まれているは、HST01 と HST02 の両方で、仮想マシンで実行されます。 アプライアンスの高可用性を実現 AD01 および AD02 は複製されたドメイン コント ローラーとフェールオーバーが発生しないようにします。 いずれかが失敗した場合、もう 1 つに既に正しいデータで使用できます。  
  
*appliance_domain*-ISCSI01  
1 つの ISCSI 仮想マシンは、接続されているストレージ (HSA01 HSA06) では、各ホストで実行されます。 この VM では、フェールオーバーされません。  
  
### <a name="hosts"></a>Hosts  
*appliance_domain*-を通じて HST01 *appliance_domain*-HST06  
PDW 管理ノードとアプライアンスのファブリックの仮想マシンをホストします。 HST03 は、オプションのパッシブ ホストです。  
  
*appliance_domain*-を通じて HSA01 *appliance_domain*-HSA08  
記憶域を持つホストには、(HSA) が接続されています。 各 HAS ホスト実行する 1 つの計算ノード VM と ISCSI VM いずれか。  
  
### <a name="cluster-for-pdw"></a>PDW のクラスター  
*appliance_domain*-WFOHST01  
PDW クラスター WFOHST01 と呼びます。 すべての物理ホストと PDW に属している仮想マシンを管理します。  
  
### <a name="direct-attached-storage"></a>直接取り付け記憶域  
*appliance_domain*-を通じて DAS01 *appliance_domain*-DAS03  
これは、コンピューティング ノードに接続されている、直接接続されたストレージです。 HP には、次の 2 つのコンピューティング ノードごとに 1 つの DAS があります。 Dell とクォンタムは、次の 3 つのコンピューティング ノードごとに 1 つの DAS をあります。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[アプライアンス構成&#40;分析プラットフォーム システム&#41;](appliance-configuration.md)  
[アプライアンスの管理タスク&#40;分析プラットフォーム システム&#41;](appliance-management-tasks.md)  
  
