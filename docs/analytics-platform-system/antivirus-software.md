---
title: ウイルス対策ソフトウェア、Analytics Platform System |Microsoft ドキュメント
description: データ センターには、ウイルス対策ソフトウェアが必要とする場合は、次のガイドラインを使用して、Analytics Platform System にウイルス対策ソフトウェアをインストールします。 会社のデータ センターの要件である場合を除き、ウイルス対策ソフトウェアをインストールしないことをお勧めします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5d9ff6848d2df43408613d41dc7a0e6f8c1b0b8c
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Analytics Platform System のウイルス対策ソフトウェア
データ センターには、ウイルス対策ソフトウェアが必要とする場合は、次のガイドラインを使用して、Analytics Platform System にウイルス対策ソフトウェアをインストールします。 会社のデータ センターの要件である場合を除き、ウイルス対策ソフトウェアをインストールしないことをお勧めします。  
  
> [!WARNING]  
> コンピューターごとおよび分析プラットフォーム システム全体のセキュリティ上のリスクを個別に評価して、各コンピューターのセキュリティ上のリスク レベルに適しているツールを選択することを強くお勧めします。 さらに、すべてのウイルス対策プロジェクトをロールアウトする前に、システム安定性とパフォーマンスのすべての変更を測定する完全読み込みで全体をテストすることをお勧めします。  
>   
> ウイルス対策ソフトウェアでは、一部のシステム リソースを実行する必要があります。 分析プラットフォーム システム上のパフォーマンスに影響があるかどうかを判断するウイルス対策ソフトウェアをインストールした後と前にテストを実行する必要があります。  
  
このトピックの内容が記載されているガイダンスに基づいて[SQL Server を実行しているコンピューター上で実行するウイルス対策ソフトウェアの選び方](http://support.microsoft.com/kb/309422)と[サポート技術情報の記事 961804](http://support.microsoft.com/kb/961804/en-us)です。  
  
## <a name="exclusion-list-for-physical-hosts"></a>物理ホストの除外リスト  
物理ホスト上のウイルス対策ソフトウェアをインストールするには、ディレクトリとプロセスの次のリストを除外します。 これらは、ウイルス対策ソフトウェアによってスキャンする必要がありますされません。  
  
**これらのディレクトリを除外するには。**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - 仮想マシンの構成ディレクトリ  
  
-   C:\Users\Public\Documents\Hyper-V\Virtual ハード_ディスク - 既定の仮想ハード ディスク ドライブのディレクトリ  
  
-   仮想ハード ディスク ドライブのディレクトリにある C:\clusterStorage  
  
**これらのプロセスを除外するには。**  
  
-   仮想マシンの管理 (Vmms.exe)  
  
-   仮想マシン ワーカー プロセス (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>仮想マシン (Vm) の除外リスト  
Vm にウイルス対策ソフトウェアをインストールするには、ディレクトリおよびファイルの次の一覧を除外します。 これらは、ウイルス対策ソフトウェアによってスキャンする必要がありますされません。  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain *-AD01**と ***appliance_domain *-AD02**  
  
-   制限はありません。  
  
**コンピューティング ノード Vm**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain *-VMM**  
  
-   制限はありません。  
  
***appliance_domain *-WDS**  
  
-   制限はありません。  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>参照  
[アプライアンスの管理タスク&#40;分析プラットフォーム システム&#41;](appliance-management-tasks.md)  
  
