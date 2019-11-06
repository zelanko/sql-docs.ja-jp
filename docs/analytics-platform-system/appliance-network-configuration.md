---
title: アプライアンスのネットワークの構成 - Analytics Platform System |Microsoft Docs
description: Analytics Platform System (APS) アプライアンスが構築された、すべてのサーバーおよび IHV の工場から該当するデバイス全体での IP アドレスの修正プログラムのセットで構成されています。 アプライアンスの配信、ごとに特定の顧客のデータ センターの要件に合わせて外部 (イーサネット) の IP アドレスを再構成する必要があります。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9bc836e3e05525b18ea994e768f65012e5c3d945
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961467"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Analytics Platform System のアプライアンスのネットワーク構成
Analytics Platform System (APS) アプライアンスが構築された、すべてのサーバーおよび IHV の工場から該当するデバイス全体での IP アドレスの修正プログラムのセットで構成されています。 アプライアンスの配信、ごとに特定の顧客のデータ センターの要件に合わせて外部 (イーサネット) の IP アドレスを再構成する必要があります。  
  
> [!NOTE]  
> PDW V1 8 IP の外部に必要な (*顧客が直面している*) ノードのラックを各コントロールの外部接続を提供するアドレス。 PDW 2012 (V2) は、アプライアンスの IP アドレス経由で外部からのすべてのコンポーネントを公開することでネットワーク通信を強化します。 このアプローチは、コストの削減し、柔軟性が向上し、データの移動、データの読み込みと Hadoop の統合を強化するより堅牢な設計を提供します。 必要な IP アドレスの数は、アプライアンスのノードの数によって異なります。 IP アドレスの大きなブロックを対応するために、顧客は PDW の別のサブネットに設定する必要があります。 このサブネット内で、最大 5 つの PDW ラックのコンポーネントに対応するための十分なの IP アドレス空間 (最大 250 個のアドレス) があります。  
  
**ネットワーク構成** ページでは、Analytics Platform System アプライアンス上のノードの外部に公開されたネットワーク設定を表示することができます。 このページは、読み取り専用です。  
  
![DWConfig アプライアンス ネットワーク](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>アプライアンス上のネットワーク構成を更新するには  
編集して、ファブリックのドメインとワークロードのドメインの IP アドレスの変更、 **AplianceInfo.xml**ファイルから、セットアップを実行します。 これは、オフライン操作です。 PDW リージョンは、IP アドレスの変更時に自動的に停止します。  
  
> [!NOTE]  
> ドメイン名では、セットアップ中に提供されており、文字で始まる 6 の英数字文字までに指定されます。 頻繁に名前付けシステムは、F、P で始まる PDW ワークロードのドメインで始まる fabric ドメインを作成します。この形式は、ファイルのヘルプ トピック全体と見なされますは必要ありません。 <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Analytics Platform System の IP アドレスを変更するには  
  
1.  使用して、**リモート デスクトップ**アプリケーションへの接続**HST01**ワークロードのドメイン管理者アカウントを使用します。  
  
2.  HST01 ノードでは、アプライアンス情報ファイルを開きます**c:\pdwinst\media\AplianceInfo.xml**します。  
  
    > [!NOTE]  
    > ファイルが存在しない場合は、新しいファイルが作成する必要があります。  
  
3.  必要に応じて、イーサネット IP 値を更新し、ファイルを保存します。  
  
4.  コマンド プロンプト ウィンドウでは、P、F、または H のドメイン名と管理者のパスワードを使用して、PDW リージョンの IP アドレスを更新する次の setup コマンドを実行します。  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>製造元の参照  
Dell のアプライアンスの詳細についてを参照してください。  
  
-   スイッチの PowerConnect 指示[Dell PowerConnect 6200 Series システム CLI 参照ガイド](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC[統合 Dell リモート アクセス コント ローラー 7 (iDRAC7) バージョン 1.30.30 ユーザー ガイド](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU の**Dell Rack PDU を従量制課金**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>関連項目  
[Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
