---
title: Windows を受け取りますが、リモート テーブルの並列データ ウェアハウス構成 |Microsoft ドキュメント
description: 購入して Parallel Data Warehouse でのリモート テーブルのコピー機能で使用するための InfiniBand ネットワークを使用して接続されているアプライアンス非 Windows システムを構成する方法について説明します。 Windows システムでは、SQL Server PDW のデータベースからリモート テーブルのコピーを受信する SQL Server データベースをホストします。 アプライアンスから別途購入、アプライアンスの InfiniBand ネットワークに接続します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7122f497b0bdebd893eec75606bbb6382e9a73
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538772"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>InfiniBand - 並列データ ウェアハウスを使用してリモート テーブルのコピーを受信する外部の Windows システムを構成します。
購入して、SQL Server PDW でリモート テーブルのコピー機能で使用するための InfiniBand ネットワークを使用して接続されているアプライアンス非 Windows システムを構成する方法について説明します。 Windows システムでは、SQL Server PDW のデータベースからリモート テーブルのコピーを受信する SQL Server データベースをホストします。 アプライアンスから別途購入、アプライアンスの InfiniBand ネットワークに接続します。  
  
> [!NOTE]  
> InfiniBand ネットワーク経由での接続は、リモート テーブルのコピーを使用する必要はありません。 イーサネット帯域幅要件を満たさない場合、イーサネット ネットワーク経由で接続を実行できます。  
  
このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください[リモート テーブルのコピー。](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>はじめに  
外部の Windows システムを構成する前に次の操作を行う必要があります。  
  
1.  購入するか、リモートのコピーを受信する Windows システムを提供します。  
  
2.  (十分な領域がある場合)、Windows システム コントロールのラックをラック閉じたりアプライアンスに十分なアプライアンスの InfiniBand ネットワークに接続することができるようにします。  
  
3.  アプライアンス ハードウェア ベンダーから InfiniBand ケーブルおよび InfiniBand ネットワーク アダプターを購入します。 エクスポートされたデータを受信するときに、フォールト トレランスのための 2 つのポートを持つネットワーク アダプターを購入することをお勧めします。 2 つのポートのネットワーク アダプターは勧めしますが、必須ではありません。  
  
## <a name="HowToWindows"></a>リモート テーブルのコピーを受信する外部の Windows システムを構成します。  
外部の Windows システムを構成するのには、次の手順を使用します。  
  
1.  InfiniBand ネットワーク アダプターを Windows システムにインストールします。  
  
2.  InfiniBand ネットワーク アダプターを InfiniBand ケーブルを使用してコントロールのラックにメインの InfiniBand スイッチに接続します。  
  
3.  インストールし、適切な Windows ドライバー InfiniBand ネットワーク アダプターを構成します。  
  
    Windows 用の InfiniBand ドライバーは、OpenFabrics Alliance、InfiniBand 仕入先の業界 consortium によって開発されています。  適切なドライバーは、InfiniBand アダプターと共に配布されたことがあります。 それ以外の場合は、ドライバーは www.openfabrics.org からダウンロードできます。  
  
4.  アダプターでは、各ポートの IP アドレスを構成します。 SMP システムは、この目的のために予約されたアドレスの範囲から静的 IP アドレスを使用する必要があります。 次のパラメーターに従って最初のポートを構成します。  
  
    -   ネットワークの IP アドレス: 172.16.132.x  
  
    -   IP サブネット マスク: 255.255.128.0  
  
    -   ホストの IP 範囲: 1 ~ 254  
  
    2 つのポートの InfiniBand ネットワーク アダプターの次のパラメーターに基づく 2 番目のポートを構成します。  
  
    -   ネットワークの IP アドレス: 172.16.132.x  
  
    -   IP サブネット マスク: 255.255.128.0  
  
    -   ホストの IP 範囲: 1 ~ 254  
  
5.  2 つのポートのアダプターを使用すると、複数の外部の Windows システムがアプライアンスに接続されている場合は、各システムに各 IP サブネット内の別のホストの番号を割り当てます。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
