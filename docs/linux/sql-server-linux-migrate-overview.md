---
title: "Linux 上の SQL Server にデータベースの移行 |Microsoft ドキュメント"
description: "このトピックでは、Linux 上の SQL Server にデータベースとデータの移行を行うためのさまざまなオプションについて説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: 
ms.workload: Inactive
ms.openlocfilehash: d07112eab83a88b4d76f6cd2c6487778abda9d80
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Linux 上の SQL Server にデータベースと構造化データを移行します

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Linux で実行されている SQL Server 2017 に、データベースとデータを移行できます。 使用する方法は、ソース データと特定のシナリオによって異なります。 次のセクションでは、さまざまな移行シナリオのベスト プラクティスを提供します。

## <a name="migrate-from-sql-server-on-windows"></a>Windows 上の SQL Server から移行します
Linux 上の SQL Server 2017 に Windows 上の SQL Server データベースを移行する場合は、SQL Server のバックアップを使用した復元をお勧めします。

1. Windows コンピューターで、データベースのバックアップを作成します。
2. バックアップ ファイルをターゲットの SQL Server の Linux コンピューターに転送します。
3. Linux コンピューター上のバックアップを復元します。 

バックアップと復元によるデータベースを移行する方法のチュートリアルで、次のトピックを参照してください。

- [Windows から Linux にSQL Server データベースを復元する](sql-server-linux-migrate-restore-database.md)

データベースを BACPAC ファイル (データベース スキーマとデータを含む圧縮ファイル) にエクスポートすることもできます。 BACPAC ファイルがある場合、Linux コンピューターにこのファイルを転送し、SQL Server にインポートできます。 詳細については、次の各トピックを参照してください。

- [SSMS または SqlPackage.exe で、データベースをエクスポートとインポートします。](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>他のデータベース サーバーから移行します
Linux 上の SQL Server 2017 に他のデータベース システム上のデータベースを移行できます。 これには、Microsoft Access、DB2、MySQL、Oracle、および Sybase のデータベースが含まれます。 このシナリオでは、Linux 上の SQL Server への移行を自動化するために、SQL Server Management Assistant (SSMA) を使用します。 詳細については、次を参照してください。 [SSMA を使用して、Linux 上の SQL Server にデータベースを移行](sql-server-linux-migrate-ssma.md)

## <a name="migrate-structured-data"></a>構造化データを移行します
生データをインポートするための手法もあります。 他のデータベースまたはデータ ソースからエクスポートされた構造化データ ファイルを利用します。 この場合、bcp ツールを使用して、データを一括挿入できます。 または、Windows の SQL Server Integration Services を実行し、Linux 上の SQL Server データベースにデータをインポートすることができます。 SQL Server Integration Services では、インポート中に、データにより複雑な変換を実行することができます。 

これらの方法の詳細については、次のトピックを参照してください。

- [Bcp を使用したデータの一括コピー](sql-server-linux-migrate-bcp.md)
- [SQL Server on Linux と SSIS による抽出、変換、およびデータの読み込み](sql-server-linux-migrate-ssis.md) 
