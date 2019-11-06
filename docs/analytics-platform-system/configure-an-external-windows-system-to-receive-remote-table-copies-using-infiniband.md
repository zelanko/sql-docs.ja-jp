---
title: リモート テーブル コピー - Parallel Data Warehouse を受け取るための Windows の構成 |Microsoft Docs
description: 購入し、Parallel Data Warehouse でのリモート テーブル コピー機能で使用するための InfiniBand ネットワークを使用して接続されている非アプライアンス Windows システムを構成する方法について説明します。 Windows システムでは、SQL Server PDW のデータベースから、リモート テーブルのコピーを受信する SQL Server データベースをホストします。 アプライアンスから個別に購入した、アプライアンスの InfiniBand ネットワークに接続します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 428dc5b4edda91f60a09a52c0326f881f257b32c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961306"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>InfiniBand、Parallel Data Warehouse を使用してリモート テーブル コピーを受け取るための外部の Windows システムを構成します。
購入して、SQL Server PDW でリモート テーブル コピー機能で使用するための InfiniBand ネットワークを使用して接続されている非アプライアンス Windows システムを構成する方法について説明します。 Windows システムでは、SQL Server PDW のデータベースから、リモート テーブルのコピーを受信する SQL Server データベースをホストします。 アプライアンスから個別に購入した、アプライアンスの InfiniBand ネットワークに接続します。  
  
> [!NOTE]  
> InfiniBand ネットワーク経由で接続では、リモート テーブルのコピーを使用するために必要ありません。 イーサネット帯域幅のニーズを満たしている場合、イーサネット ネットワーク経由で接続を実行できます。  
  
このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください[リモート テーブルのコピー。](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>はじめに  
外部の Windows システムを構成する前にする必要があります。  
  
1.  購入またはリモートのコピーを受信する Windows システムを提供します。  
  
2.  (十分な領域がある場合)、Windows システム コントロールのラックをラックまたは閉じてアプライアンスに十分なアプライアンスの InfiniBand ネットワークに接続することができます。  
  
3.  InfiniBand ケーブルおよび InfiniBand ネットワーク アダプターをアプライアンスのハードウェア ベンダーから購入します。 エクスポートされたデータを受信するときに、フォールト トレランスの 2 つのポートのネットワーク アダプターを購入することをお勧めします。 2 つのポートのネットワーク アダプターを勧めしますが、必須ではありません。  
  
## <a name="HowToWindows"></a>リモート テーブル コピーを受け取るため、外部の Windows システムを構成します。  
外部の Windows システムを構成するには、次の手順を使用します。  
  
1.  Windows システムに、InfiniBand ネットワーク アダプターをインストールします。  
  
2.  InfiniBand ケーブルを使用してコントロールのラックにメインの InfiniBand スイッチには、InfiniBand ネットワーク アダプターを接続します。  
  
3.  インストールし、InfiniBand ネットワーク アダプターの適切な Windows ドライバーを構成します。  
  
    Windows 用の InfiniBand ドライバーは、OpenFabrics Alliance、InfiniBand ベンダーに業界コンソーシアムによって開発されています。  適切なドライバーは、InfiniBand アダプターと共に配布されたことがあります。 それ以外の場合は、ドライバーは www.openfabrics.org からダウンロードできます。  
  
4.  アダプターのポートごとに IP アドレスを構成します。 SMP システムは、この目的のために予約されたアドレスの範囲から静的 IP アドレスを使用する必要があります。 次のパラメーターに基づく最初のポートを構成します。  
  
    -   ネットワークの IP アドレス:172.16.132.x  
  
    -   IP サブネット マスク:255.255.128.0  
  
    -   ホストの IP 範囲:1-254  
  
    2 つのポートでの InfiniBand ネットワーク アダプターには、次のパラメーターに従って 2 つ目のポートを構成します。  
  
    -   ネットワークの IP アドレス:172.16.132.x  
  
    -   IP サブネット マスク:255.255.128.0  
  
    -   ホストの IP 範囲:1-254  
  
5.  2 つのポートのアダプターを使用すると、または、複数の外部の Windows システムがアプライアンスに接続されている場合、は、各 IP サブネット内で別のホストの数を各システムに割り当てます。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
