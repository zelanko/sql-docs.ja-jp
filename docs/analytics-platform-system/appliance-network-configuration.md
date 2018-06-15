---
title: アプライアンス ネットワークの構成 - Analytics Platform System |Microsoft ドキュメント
description: Analytics Platform System (APS) アプライアンスを構築およびすべてのサーバーと IHV の工場から、該当するデバイス全体での IP アドレスの修正プログラムのセットで構成します。 アプライアンスの配信、ごとには、特定の顧客のデータ センターの要件に一致する (イーサネット) の外部 IP アドレスを再構成する必要があります。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2db040c63d3c31f93cd0b72e48422e806aef01e0
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539312"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Analytics Platform System のアプライアンス ネットワークの構成
Analytics Platform System (APS) アプライアンスを構築およびすべてのサーバーと IHV の工場から、該当するデバイス全体での IP アドレスの修正プログラムのセットで構成します。 アプライアンスの配信、ごとには、特定の顧客のデータ センターの要件に一致する (イーサネット) の外部 IP アドレスを再構成する必要があります。  
  
> [!NOTE]  
> PDW V1 必要 8 IP 外部 (*顧客が直面している*) を各コントロールの外部接続を提供するアドレスのラックのノードです。 PDW 2012 (V2) は、IP アドレスを使用して外部アプライアンスのすべてのコンポーネントを公開することでネットワーク通信を強化します。 この方法は、コストが削減され、柔軟性、およびデータの移動、データの読み込みと Hadoop の統合を強化するより堅牢なデザインを提供します。 必要な IP アドレスの数は、アプライアンス内のノードの数と HDInsight などの機能の存在に依存します。 対応するための IP アドレスの大きなブロックをお客様は PDW の別のサブネットに設定する必要があります。 このサブネット内で、最大 5 つの PDW ラックのコンポーネントに対応するための十分なの IP アドレス空間 (最大 250 個のアドレス) があります。  
  
**ネットワーク構成** ページでは、Analytics Platform System アプライアンス上のノードの外部に公開されたネットワーク設定を表示することができます。 このページは、読み取り専用です。  
  
![DWConfig アプライアンス ネットワーク](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>アプライアンス上のネットワーク構成を更新するには  
編集して、ファブリック ドメイン、ワークロードのドメイン、および HDInsight のドメインの IP アドレスを変更、 **AplianceInfo.xml**ファイルとセットアップを実行します。 これは、オフライン操作です。 PDW と HDInsight (存在する場合) の両方の地域は IP アドレスの変更時に自動的に停止されます。  
  
> [!NOTE]  
> ドメイン名は、セットアップ時に指定、最大で 6 文字の英数字文字で始まるように指定されます。 頻繁な名前付けシステム F、P で始まる PDW ワークロードのドメインおよび H. で始まる HDInsight ドメインで始まるファブリック ドメインを作成します。この形式は、ファイルのヘルプ トピック全体と見なされますが、必須ではありません。 <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>Analytics Platform System の IP アドレスを変更するには  
  
1.  使用して、**リモート デスクトップ**アプリケーションへの接続**HST01**ワークロード ドメイン管理者アカウントを使用します。  
  
2.  HST01 ノードでファイルを開く、アプライアンス情報で**c:\pdwinst\media\AplianceInfo.xml**です。  
  
    > [!NOTE]  
    > ファイルが存在しない場合は、新しいファイルが作成する必要があります。  
  
3.  必要に応じて、イーサネットの IP 値を更新し、ファイルを保存します。  
  
4.  コマンド プロンプト ウィンドウで、H F/P/ドメイン名と管理者のパスワードを使用して、PDW 地域の IP アドレスを更新して、次のセットアップ コマンドを実行します。  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>製造元の参照  
Dell アプライアンスに関する追加情報を参照してください。  
  
-   PowerConnect スイッチ指示[Dell PowerConnect 6200 シリーズ システム CLI ガイドを参照します。](http://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC[統合 Dell リモート アクセス コント ローラー 7 (iDRAC7) バージョン 1.30.30 ユーザーズ ガイド 』](http://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU の**Dell にラック PDU が従量制課金**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>参照  
[構成マネージャーを起動&#40;分析プラットフォーム システム&#41;](launch-the-configuration-manager.md)  
  
