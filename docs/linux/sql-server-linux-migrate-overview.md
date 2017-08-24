---
title: "Linux 上の SQL Server にデータベースの移行 |Microsoft ドキュメント"
description: "このトピックでは、Linux 上のデータベースの移行とデータを SQL Server のさまざまなオプションについて説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1619489d-377a-4f32-8930-d4f536539689
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 61b4ba948df071768380d4a6f2b4ddc4421692d8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrate-databases-and-structured-data-to-sql-server-on-linux"></a>Linux 上の SQL Server にデータベースと構造化データを移行します。 

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Linux で実行されている SQL Server 2017 RC2 には、データベースとデータを移行できます。 使用する方法は、ソース データと特定のシナリオによって異なります。 次のセクションでは、さまざまな移行シナリオのベスト プラクティスを提供します。

## <a name="migrate-from-sql-server-on-windows"></a>Windows 上の SQL Server からの移行します。
Linux 上の SQL Server 2017 に Windows 上の SQL Server データベースを移行する場合は、推奨される手法は、SQL Server のバックアップを使用して復元します。

1. Windows コンピューターで、データベースのバックアップを作成します。
2. バックアップ ファイルをターゲット SQL Server の Linux コンピューターに転送します。
3. Linux コンピューター上のバックアップを復元します。 

バックアップと復元によるデータベースを移行する方法のチュートリアルでは、次のトピックを参照してください。

- [SQL Server データベースを復元する Windows から Linux](sql-server-linux-migrate-restore-database.md)です。

データベースを BACPAC ファイル (データベース スキーマとデータを含む圧縮ファイル) にエクスポートすることもできます。 BACPAC ファイルがある場合、Linux コンピューターにこのファイルを転送し、SQL Server にインポートできます。 詳細については、次の各トピックを参照してください。

- [エクスポートし、SSMS または SqlPackage.exe でデータベースをインポートします。](sql-server-linux-migrate-ssms.md)

## <a name="migrate-from-other-database-servers"></a>他のデータベース サーバーからの移行します。
Linux 上の SQL Server 2017 に他のデータベース システム上のデータベースを移行できます。 これには、Microsoft Access、DB2、MySQL、Oracle、および Sybase のデータベースが含まれます。 このシナリオでは、Linux 上の SQL Server への移行を自動化するのに、SQL Server Management Assistant (SSMA) を使用します。 詳細については、次を参照してください。 [Linux に SQL Server にデータベースを移行する使用 SSMA](sql-server-linux-migrate-ssma.md)です。  

## <a name="migrate-structured-data"></a>構造化データを移行します。
生データをインポートするための手法もあります。 他のデータベースまたはデータ ソースからエクスポートされたデータ ファイルを構造する可能性があります。 この場合、bulk insert のデータを bcp ツールを使用できます。 または、Linux 上の SQL Server データベースにデータをインポートする Windows の SQL Server Integration Services を実行することができます。 SQL Server Integration Services では、インポート中に、データでより複雑な変換を実行することができます。 

これらの方法の詳細については、次のトピックを参照してください。

- [Bcp を使用したデータの一括コピー](sql-server-linux-migrate-bcp.md)
- [抽出、変換、および SQL Server on Linux と SSIS のデータを読み込む](sql-server-linux-migrate-ssis.md) 

