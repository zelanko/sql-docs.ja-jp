---
title: Analytics Platform System のアプライアンス物理コンポーネント |Microsoft Docs
description: 名前と PDW およびアプライアンス ファブリックの物理的なコンポーネントの説明。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fb7ad8715d3f7a885bc48f6bdcc7f1ec2842f269
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960426"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Analytics Platform System のアプライアンス物理コンポーネント
名前と PDW およびアプライアンス ファブリックの物理的なコンポーネントの説明。 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>コンポーネント図  
物理コンポーネントと 6 コンピューティング ノードのアプライアンスの最初のラックに配置されている名前が表示されます。  
  
![PDW リージョン コンポーネント名 - HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames HP")  
  
PDW コンポーネントの実際の名前は、ダッシュ、コンポーネント名の後に続く、PDW リージョン名前です。 たとえば、PDW リージョン名が PDW123 の場合は、実際の名前は**PDW123 CTL01**、 **PDW123 CMP01**など。  
  
同様に、アプライアンス ファブリック コンポーネントの実際の名前は、ダッシュ、コンポーネント名の後に続く、アプライアンスのドメインです。 たとえば、アプライアンスのドメインが FSW123 の場合は、アプライアンス ファブリックの Vm は**FSW123 WDS**、 **FSW123 AD01**、 **FSW123 VMM**など。  
  
ここで、6 つのコンピューティング ノードで PDW リージョンの統合ビューです。  
  
![PDW コンポーネント名](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>PDW コンポーネント  
PDW の仮想マシンは、PDW 領域の一部です。  
  
*PDW_region*-CTL01  
コントロールのノードを実行する仮想マシン。 これにより、HST01 で実行され、HST02 にフェールオーバーできます。  
  
> [!WARNING]  
> SQL Server PDW は、HYPER-V マネージャーを使用して、CTL01 仮想マシンのスナップショットの作成をサポートしていません。 スナップショットは、仮想マシンのバックアップをフェールオーバーしようとすると、エラーが発生すると、ローカル ストレージに依存します。 スナップショットを作成する可能性もあります信頼性の問題の他の VM とパッシブのサーバーへのフェールオーバーをします。  
  
*PDW_region*-を通じて CMP01 *PDW_Region*-CMP06  
コンピューティング ノードを実行する仮想マシン。 この 6 コンピューティング ノードの図では実行 HSA06 を使用して、ホスト HSA01 CMP06 経由で Vm CMP01 ノードをそれぞれ計算します。  
  
## <a name="fabric"></a>アプライアンス ファブリック コンポーネント  
これらのコンポーネントは、アプライアンス ファブリックの一部です。  
  
### <a name="virtual-machines"></a>仮想マシン  
*appliance_domain*-WDS  
Analytics Platform System を使用する Windows 展開サービス (WDS)、この仮想マシンがホストでは、アプライアンス ネットワーク経由で Windows オペレーティング システムを展開します。 アプライアンスのホストが事前構成済みの IP アドレスをしなくても、アプライアンスのネットワークに参加できるように、DHCP サービスもホストします。  
  
*Appliance_domain*-WDS の仮想マシンが HST01 で実行し、HST02 にフェールオーバーできます。 WDS の仮想マシンと、VMM の仮想マシンは、アプライアンスのインストール中に物理ホストで Windows を展開します。 WDS と VMM は、アプライアンスのライフ サイクル中にホストを交換などの操作を実行します。  
  
*appliance_domain*VMM  
Virtual Machine Manager (VMM) では、仮想マシンで実行され、HST02 にフェールオーバーできます。 VMM では、物理ホスト上のオペレーティング システムを展開する System Center をホストします。 VMM では、すべてのホストとバーチャル マシンでの Windows 更新プログラムの削除を適用または Windows Server Update Services (WSUS) も提供します。  
  
*appliance_domain*-AD01、 *appliance_domain*-AD02  
Active Directory Domain Services ドメイン ネーム システム (DNS) が含まれている HST01 と HST02 の両方では、仮想マシンでは実行されます。 アプライアンスの高可用性のためには、AD01 と AD02 はレプリケートされたドメイン コント ローラーとそのフェールオーバーにを実行します。 いずれかが失敗した場合は、もう 1 つは、正しいデータで使用可能な既にです。  
  
*appliance_domain*-ISCSI01  
1 つの ISCSI 仮想マシンは、各ホストに接続されているストレージ (HSA01 HSA06) を実行します。 この VM は、フェールオーバーではありません。  
  
### <a name="hosts"></a>Hosts  
*appliance_domain*-を通じて HST01 *appliance_domain*-HST06  
PDW 管理ノードおよびアプライアンス ファブリックの仮想マシンをホストします。 HST03 は、オプションのパッシブ ホストです。  
  
*appliance_domain*-を通じて HSA01 *appliance_domain*-HSA08  
接続されているストレージ (HSA) でホストします。 各 HAS ホストの実行 1 コンピューティング ノード VM と VM の ISCSI いずれか。  
  
### <a name="cluster-for-pdw"></a>PDW のクラスター  
*appliance_domain*-WFOHST01  
PDW クラスター WFOHST01 と呼びます。 すべての物理ホストと PDW に属している仮想マシンを管理します。  
  
### <a name="direct-attached-storage"></a>直接接続されたストレージ  
*appliance_domain*-を通じて DAS01 *appliance_domain*-DAS03  
これは、コンピューティング ノードに接続されている、直接接続ストレージです。 HP では、2 つのコンピューティング ノードごとに 1 つの DAS があります。 Dell とクォンタムは、次の 3 つのコンピューティング ノードごとに 1 つの DAS をあります。  
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[アプライアンスの構成&#40;Analytics Platform System&#41;](appliance-configuration.md)  
[アプライアンスの管理タスク&#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
