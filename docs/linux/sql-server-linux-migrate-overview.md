---
title: SQL Server on Linux へのデータベースの移行 |Microsoft Docs
description: この記事では、Linux 上のデータベースの移行とデータを SQL Server のさまざまなオプションについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: sql-linux
ms.openlocfilehash: c7b7225ae4e981244ee06194ea9e4ef595ba283d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045130"
---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Linux 上の SQL Server にデータベースと構造化データを移行する 

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Linux で実行されている SQL Server 2017 に、データベースとデータを移行できます。 使用する方法は、ソース データと特定のシナリオによって異なります。 次のセクションでは、さまざまな移行シナリオのベスト プラクティスを提供します。

## <a name="migrate-from-sql-server-on-windows"></a>Windows 上の SQL Server から移行
Linux 上の SQL Server 2017 に Windows 上の SQL Server データベースを移行する場合は、SQL Server のバックアップと復元を使用した手法をお勧めします。

1. Windows コンピューター上のデータベースのバックアップを作成します。
2. ターゲットの SQL Server Linux マシンをバックアップ ファイルを転送します。
3. Linux マシン上のバックアップを復元します。 

バックアップと復元によりデータベースを移行する方法のチュートリアルについては、次のトピックを参照してください。

- [Windows から Linux にSQL Server データベースを復元する](sql-server-linux-migrate-restore-database.md)。

データベースを BACPAC ファイル (データベース スキーマとデータを含む圧縮ファイル) にエクスポートすることもできます。 BACPAC ファイルがある場合は、Linux コンピューターにこのファイルを転送し、SQL Server にインポートします。 詳細については、次の各トピックを参照してください。

- [SSMS または SqlPackage.exe で、データベースをエクスポートおよびインポートします。](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>他のデータベース サーバーからの移行
Linux 上の SQL Server 2017 に他のデータベース システム上のデータベースを移行できます。 これには、Microsoft Access、DB2、MySQL、Oracle、および Sybase のデータベースが含まれます。 このシナリオでは、Linux 上の SQL Server への移行を自動化するために、SQL Server Management Assistant (SSMA) を使用します。 詳細については、次を参照してください。 [SSMA を使用して、Linux 上の SQL Server にデータベースを移行](sql-server-linux-migrate-ssma.md)。  

## <a name="migrate-structured-data"></a>構造化データの移行
生データをインポートするための手法もあります。 他のデータベースまたはデータ ソースからエクスポートされた構造化データ ファイルを利用します。 この場合、bcp ツールを使用して、データを一括挿入できます。 または、Windows の SQL Server Integration Services を実行し、Linux 上の SQL Server データベースにデータをインポートすることができます。 SQL Server Integration Services では、インポート中に、データにより複雑な変換を実行することができます。 

これらの方法の詳細については、次のトピックを参照してください。

- [Bcp を使用したデータの一括コピー](sql-server-linux-migrate-bcp.md)
- [SQL Server on Linux と SSIS による抽出、変換、およびデータの読み込み](sql-server-linux-migrate-ssis.md) 
