---
title: アプライアンスのインストールし、構成 - Analytics Platform System |Microsoft Docs
description: Analytics Platform System (APS) アプライアンスの管理者を設定して、新しいアプライアンスの使用を開始する初期手順について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1f32cbeccb9a71d1d4c801443b40df5a762b8f38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961487"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Analytics Platform System のアプライアンスのインストールと構成
Analytics Platform System (APS) アプライアンスの管理者を設定して、新しいアプライアンスの使用を開始する初期手順について説明します。  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1.ハードウェアをインストールします。  
新しいアプライアンスは、データ センターでドッキング ステーションにパレットに提供されます。  
  
> [!IMPORTANT]  
> 場合によっては、IHV は開梱、ラック取り付け、およびデータ センター内のアプライアンスに接続します。 かどうか、これらの手順は必要ありませんしに進んで、 [3。アプライアンスを構成](#ConfigureAppliance)以下のセクション。  
  
IHV がハードウェアのインストールを実行していない場合は、次の手順を使用して、ハードウェアをインストールします。  
  
|||  
|-|-|  
|**Task**|**[説明]**|  
|ドキュメントを確認します。|独立系ハードウェア ベンダー (IHV) からすべての必要なドキュメントや情報を入手したことを確認します。 参照してください[IHV から取得する情報&#40;Analytics Platform System&#41;](information-to-obtain-from-your-ihv.md)します。|  
|ハードウェアをインストールします。|データ センターがアプライアンスに対応できることを確認します。 アプライアンスのコンポーネントをデータ センターに移動します。 ネットワーク スイッチ、Pdu、ラック設置、ケーブル接続します。 参照してください[ハードウェアの設置&#40;Analytics Platform System&#41;](hardware-installation.md)します。|  
  
## <a name="PowerOnAppliance"></a>2.アプライアンスの電源を入れます  
  
|||  
|-|-|  
|**Task**|**[説明]**|  
|アプライアンスの電源を入れます|エラーが発生しないことを確認する必要に応じて、待機している、必要な順序で各アプライアンス コンポーネント ノードの電源を入れます。|  
  
## <a name="ConfigureAppliance"></a>3.アプライアンスを構成します。  
  
|||  
|-|-|  
|**Task**|**[説明]**|  
|||  
|SQL Server の PDW を使用して、アプライアンスを構成する**Configuration Manager**|Configuration Manager を使用すると、ご使用のアプライアンスのアプライアンス パスワード、タイム ゾーン、ネットワークとファイアウォールの設定、セキュリティ証明書、およびパフォーマンスおよびその他の設定を設定できます。 参照してください[アプライアンス構成&#40;Analytics Platform System&#41;](appliance-configuration.md)します。|  
  
> [!WARNING]  
> SQL Server の PDW を使用して構成の変更を確立する必要がありますのみ**Configuration Manager**します。 使用しない変更**Configuration Manager**はサポートされていません。 たとえば、SQL Server PDW アプライアンスは、英語 (米国) 言語の設定のみをサポートします。  
  
## <a name="SoftwareServicing"></a>4.ソフトウェアのサービスを設定します。  
  
|||  
|-|-|  
|**Task**|**[説明]**|  
|SQL Server PDW の更新プログラムを適用します。|(省略可能)SQL Server PDW ソフトウェアを最新バージョンに更新する 1 つまたは複数の SQL Server PDW の更新を適用する必要があります。 参照してください[Analytics Platform System の修正プログラムを適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)します。|  
|Windows Server Update Services の構成|ソフトウェアをサポートするための Windows Server Update Services から更新プログラムを受信するアプライアンスを構成します。 参照してください[ダウンロードし、Microsoft 更新プログラムを適用&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)します。|  
  
## <a name="NextSteps"></a>次の手順  
すべての前の手順を完了した後、アプライアンスが使用できる状態にします。 ユーザーやその他の担当者、場所は、次のタスクを開始できます。  
  
|||  
|-|-|  
|**Task**|**[説明]**|  
|SQL Server PDW のドライバーのインストールし、接続の構成|SQL Server Data Tools、sqlcmd、ビジネス インテリジェンスのソフトウェア、またはその他のツールを使用して SQL Server PDW に接続するローカル コンピューターを構成します。 <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|ログオンとサーバーの役割を作成し、アクセス許可を割り当てる|計画し、適切なアクセス許可を持つ SQL Server PDW にログオンするユーザーをログオンとサーバーの役割を作成します。 <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Azure データ管理ゲートウェイを構成します。|ゲートウェイには、AP データをセキュリティで保護された OData フィードとして公開することで、オンプレミスの AP のデータにアクセスする Azure のユーザーができます。 ゲートウェイは、既にコントロールのノードにインストールされます。 構成に関するマイクロソフトを求めてください。|  
|モニターのクエリとアプライアンスのユーザー|管理コンソールおよびその他のリソースを使用して、クエリとアプライアンスのユーザーが監視されます。 参照してください[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|SQL Server PDW にデータを読み込む|ご使用のアプライアンスにデータを読み込みます。 <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|ディザスター リカバリー計画を作成します。|ハードウェア障害からデータを保護する方法を計画またはデータが上書きされます。 定期的なバックアップを使用してプランを作成し、データの破損または損失が発生した場合のプランを復元します。 <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|アプライアンスを監視します。|システム ビュー、ログ、および管理コンソールを使用して、アプライアンスの状態、ヘルス、およびパフォーマンスを監視します。 修正または問題を報告します。 参照してください[モニター アプライアンスの正常性状態&#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)します。|  
