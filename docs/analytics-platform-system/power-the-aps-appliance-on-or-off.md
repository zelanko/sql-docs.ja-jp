---
title: 電源をオンまたはオフ、Analytics Platform System appliance |Microsoft Docs
description: Analytics Platform System の電源をオンまたはオフのアプライアンス
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d24f808365a8a04fdc6b469a8eaac98c208c19e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960240"
---
# <a name="power-the-appliance-on-or-off-for-analytics-platform-system"></a>Analytics Platform System の電源をオンまたはオフのアプライアンス
このトピックでは、どの電源オフ、Analytics Platform Systemappliance 電源またはを実行している Parallel Data Warehouse について説明します。 使用して、このトピックで Analytics Platform System appliance が移動したとき、または電源にアプライアンスで致命的な電源障害が発生しました。  
  
アプライアンスの電源オンとオフは、開始と停止のアプライアンスのサービスと同じではありません。 そのサブジェクトについては、次を参照してください。 [PDW のサービス状態&#40;Analytics Platform System&#41;](pdw-services-status.md)します。 電源をオンまたはオフ、SQL Server 2008 Parallel Data Warehouse については、SQL Server 2008 Parallel Data Warehouse のヘルプ ファイルを参照してください。 電源をオンまたはオフ、SQL Server 2012 AU1 または AU2 Parallel Data Warehouse については、これらのバージョンのヘルプ ファイルを参照してください。  
  
接続は、ローカル接続されているデバイス (KVM) を使用してこれらの手順では、SQL Server PDW ノードへの接続を指定するときに、またはリモート デスクトップを使用したリモート接続します。 いくつかの操作が (オン、電源スイッチ)、物理マシンとシャット ダウン) などの一部にする必要がありますは物理または Windows を使用してコマンドします。  
  
SQL Server PDW ノードへの接続は、ノードとの間に割り当てられている IP アドレスを使用して行われたことができます、 **HST01**コンピューターを使用して、**フェールオーバー クラスター マネージャー** (**cluadmin.msc**)または **、HYPER-V Manager** (**virtmgmt.msc**) アプリケーションとノードの名前を右クリックします。  
  
## <a name="PowerOff"></a>電源オフ、アプライアンス  
  
### <a name="before-you-begin"></a>アンインストールの準備  
アプライアンスを切る前に、アプライアンス上のすべてのアクティビティを終了する必要があります。 すべてのアクティビティを終了するには。  
  
-   使用して、**セッション**現在のユーザーを識別するために、管理者コンソールのページ。 パートナーに連絡し、ログオフするように依頼します。  
  
-   必要なを使って、 **KILL**クライアント接続の終了を強制するステートメント。 強制終了時に注意を使用して接続します。 実行時間の長いの更新など、一部のトランザクション プロセスが中断されたときにする必要があります SQL Server の前にロールバック アクティビティ完了できます、データベースの復旧。 ロールバックして、部分的に完了した更新や削除は時間がかかることができます。  
  
### <a name="to-power-off-the-appliance"></a>アプライアンスの電源を切ります  
  
> [!WARNING]  
> 正確な順序ですべての手順を実行する必要があり、各手順は次の手順を実行すると、前に明記されない限り、完了する必要があります。 誤順序のまたは各手順を完了するを待たずに手順を実行すると、後で、アプライアンスの電源投入時にエラーが発生することができます。  
  
1.  PDW 管理ノードに接続 ( **_PDW_region_-CTL01** )、Analytics Platform System appliance ドメイン管理者アカウントを使用してログインします。  
  
2.  実行`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe`を開く、 **Configuration Manager**します。  
  
3.  Configuration Manager では、下、**並列データ ウェアハウスのトポロジ** メニューのをクリックして、**サービス状態**タブをクリックし、をクリックして**リージョンの停止**PDW サービスを停止します。   
  
4.  接続する **_appliance_domain_-HST01**アプライアンスのドメイン管理者アカウントを使用してログインします。  
  
5.  使用して、**フェールオーバー クラスター マネージャー**への接続、  **_appliance_domain_-WFOHST01** 、自動的に接続された場合は、クラスターし、ナビゲーション ウィンドウで次のようにクリックします。**ロール**します。 **ロール**ウィンドウ。  
  
    1.  仮想マシンをすべて選択します。 それを右クリックして**シャット ダウン**します。  
  
    2.  すべての選択した Vm をシャット ダウンを完了するまで待ちます。  
  
6.  閉じる、**フェールオーバー クラスター マネージャー**アプリケーション。  
  
7. 除くすべてのサーバーをシャット ダウン **_appliance_domain_-HST01**します。  
  
8. シャット ダウン、  **_appliance_domain_-HST01**サーバー。  
  
9. 配電ユニット (Pdu) をシャット ダウンします。  
  
## <a name="PowerOn"></a>アプライアンスの電源を入れます  
  
### <a name="to-power-on-the-appliance"></a>アプライアンスの電源を  
  
> [!WARNING]  
> 正確な順序ですべての手順を実行する必要があり、各手順は次の手順を実行すると、前に明記されない限り、完了する必要があります。 誤順序のまたは各手順を完了するを待たずに手順を実行すると、スタートアップ エラーが発生することができます。  
  
1.  自動的に起動するには、電力配分装置 (PDU) とスイッチの待機の電源を入れます。  
  
2.  電源オン、  **_appliance_domain_-HST01**サーバー。  
  
3.  ログイン **_appliance_domain_-HST01**アプライアンスのドメイン管理者として。  
  
4.  開始、 **、HYPER-V Manager**プログラム (**virtmgmt.msc**) への接続と **_appliance_domain_-HST01**既定で接続されていない場合。  
  
    1.  ため、名前で接続できない場合、  **_PDW_region_-AD01**が実行されていない IP アドレスを使用して接続を再試行してください。  
  
    2.  **仮想マシン**ウィンドウで、検索 **_PDW_region_-AD01**が実行されていることを確認します。 ない場合は、この VM を起動しが完全に起動するまで待機します。  
  
5.  アプライアンス内のサーバーの残りの部分の電源を入れます。  
  
6.  留まった**HST01**から、アプライアンスのドメイン管理者としてログオンして **、HYPER-V Manager**:  
  
    1.  接続する **_appliance_domain_-HST02**します。  
  
    2.  **仮想マシン**ウィンドウで、検索 **_PDW_region_-AD02**が実行されていることを確認します。  ない場合は、この VM を起動しが完全に起動するまで待機します。  
  
7.  使用して、**フェールオーバー クラスター マネージャー**への接続、  **_appliance_domain_-WFOHST01**クラスターの場合は自動的に接続し、 **ナビゲーション**ウィンドウで、をクリックして**ロール**します。 **ロール**ウィンドウ。  
  
    1.  をクリックし、右クリック、すべての仮想マシンを複数選択**開始**します。  
  
    2.  以降、次の手順に進む前に [完了] を選択したすべての Vm を待ちます。  
  
    3.  フェールオーバーされる Vm の必要に応じて、シャット ダウンして、移動したり、適切なプライマリ ホスト上でそれらを再起動します。  
  
8. 切断**HST01**たい場合。  
  
9. 接続する **_PDW_region_-CTL01**アプライアンスのドメイン管理者アカウントを使用します。  
  
10. 実行`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe`を起動する、 **Configuration Manager**します。  
  
11. **Configuration Manager**の**並列データ ウェアハウスのトポロジ** メニューのをクリックして、**サービス状態**タブをクリックし、をクリックして**開始リージョン**PDW サービスを開始します。  
  
### <a name="to-verify-the-appliance-health"></a>アプライアンスの正常性を確認するには  
アプライアンスが開始すると、開く、**管理コンソール**エラー状態を示す可能性がある警告の正常性ページを確認します。 詳細については、次を参照してください。[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)します。  
  
## <a name="see-also"></a>参照  
[アプライアンスの管理タスク&#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
