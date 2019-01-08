---
title: ウイルス対策ソフトウェア、Analytics Platform System |Microsoft Docs
description: データ センターには、ウイルス対策ソフトウェアが必要とする場合は、次のガイドラインを使用して、Analytics Platform System にウイルス対策ソフトウェアをインストールします。 データ センターの確実な要件である場合を除き、ウイルス対策ソフトウェアをインストールしないことをお勧めします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c5b9a1eddf8bf06a9d9e5b59754b2c6a34b94267
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524469"
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Analytics Platform System のウイルス対策ソフトウェア
データ センターには、ウイルス対策ソフトウェアが必要とする場合は、次のガイドラインを使用して、Analytics Platform System にウイルス対策ソフトウェアをインストールします。 データ センターの確実な要件である場合を除き、ウイルス対策ソフトウェアをインストールしないことをお勧めします。  
  
> [!WARNING]  
> 個別に各コンピューターと、全体として、Analytics Platform System は、セキュリティ上のリスクを評価して、各コンピューターのセキュリティ上のリスク レベルの適切なツールを選択することを強くお勧めします。 また、ウイルス対策、プロジェクトをロールアウトする前に、安定性とパフォーマンスのすべての変更を測定する完全な負荷の下でシステム全体をテストすることをお勧めします。  
>   
> ウイルス対策ソフトウェアでは、一部のシステム リソースを実行する必要があります。 Analytics Platform System のパフォーマンスに影響があるかどうかを判断するウイルス対策ソフトウェアをインストールした後と前にテストを実行する必要があります。  
  
このトピックではガイダンスに基づいて[SQL Server を実行しているコンピューターで実行するウイルス対策ソフトウェアを選択する方法](https://support.microsoft.com/kb/309422)と[サポート技術情報の記事 961804](https://support.microsoft.com/kb/961804/en-us)します。  
  
## <a name="exclusion-list-for-physical-hosts"></a>物理ホストの除外リスト  
物理ホスト上のウイルス対策ソフトウェアをインストールするには、ディレクトリとプロセスの次のリストを除外します。 これらは、ウイルス対策ソフトウェアによってスキャンされませんする必要があります。  
  
**これらのディレクトリを除外するには。**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - 仮想マシンの構成ディレクトリ  
  
-   C:\Users\Public\Documents\Hyper-V\Virtual のハード ディスクの既定の仮想ハード ディスク ドライブのディレクトリ  
  
-   C:\clusterStorage - 仮想ハード ディスク ドライブのディレクトリ  
  
**これらのプロセスを除外するには。**  
  
-   仮想マシンの管理 (Vmms.exe)  
  
-   仮想マシン ワーカー プロセス (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>仮想マシン (Vm) の除外リスト  
Vm 上のウイルス対策ソフトウェアをインストールするには、ディレクトリおよびファイルの次の一覧を除外します。 これらは、ウイルス対策ソフトウェアによってスキャンされませんする必要があります。  
  
**_PDW_region_-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_-AD01**と **_appliance_domain_-AD02**  
  
-   制限なし  
  
**コンピューティング ノード Vm**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_VMM**  
  
-   制限なし  
  
**_appliance_domain_-WDS**  
  
-   制限なし  
  
**_appliance_domain_-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>参照  
[アプライアンスの管理タスク&#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
