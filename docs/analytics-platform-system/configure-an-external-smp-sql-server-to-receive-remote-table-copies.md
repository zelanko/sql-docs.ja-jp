---
title: リモート テーブル コピー - Parallel Data Warehouse を受け取るための SQL Server の構成 |Microsoft Docs
description: Parallel Data Warehouse からリモート テーブル コピーを受信する外部 SMP SQL Server インスタンスを構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3ad1ee005f5d28e7477fab7c1abe7ed4074e233d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961292"
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies---parallel-data-warehouse"></a>リモート テーブル コピー - Parallel Data Warehouse を受け取るため、外部 SMP SQL Server の構成します。
Parallel Data Warehouse からリモート テーブル コピーを受信する外部の SQL Server インスタンスを構成する方法について説明します。  

このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください。[リモート テーブル コピー](remote-table-copy.md)します。  
  
## <a name="before-you-begin"></a>はじめに  
外部の SQL Server を構成する前にする必要があります。  
  
-   SQL Server 2008 Enterprise Edition またはそれ以降のバージョンをインストールまたは既にインストールされている Windows システムがあります。 」の説明に従って、Windows システムを構成する必要があります既に[構成、外部 Windows システムに表示されるリモート テーブル コピーを使用して InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)します。  
  
-   SQL Server インスタンスと、Windows システムを構成する機能を Windows の管理者アカウント。  
  
-   SQL Server ログイン アカウント (SQL Server が既にインストールされている) 場合のログインを作成し、変換先のデータベースでのアクセス許可を付与することができます。  
  
## <a name="HowToSQLServer"></a>リモート テーブル コピーを受け取るため、外部 SMP SQL サーバーを構成します。  
リモート テーブル コピー機能では、Windows システムで実行されている外部 SMP SQL Server データベースに SQL Server PDW アプライアンスからテーブルをコピーします。 リモート テーブル コピーを受け取るための外部の Windows システムを構成した後は、次の手順は、インストールして、Windows システム上に SQL Server を構成するは。  
  
SQL Server を構成するには、次の手順を使用します。  
  
1.  Windows システムでは、SQL Server 2008 Enterprise Edition またはそれ以降のバージョンをインストールします。 これは、SMP の SQL Server と呼ばれます。  
  
2.  固定の TCP ポートで TCP/IP 接続を受け入れるように SQL Server を構成します。 この構成では、既定で無効にし、SMP の SQL Server に接続する SQL Server PDW の許可を有効にする必要があります。  
  
3.  Windows ファイアウォールを無効にするか、有効になっている Windows ファイアウォールで動作するように、SMP SQL Server の TCP ポートを構成します。  
  
4.  SQL Server 認証モードを許可する SQL Server を構成します。 並列データをエクスポート常に SQL Server アカウントを使用して認証します。  
  
5.  SMP の SQL server 認証に使用される SQL Server アカウントを決定します。 そのアカウントの作成、削除、および並列のデータのエクスポート操作で転送先データベース内のテーブルにデータを挿入するための権限を付与します。  
  
## <a name="BPSQLConfig"></a>リモート テーブルのコピーの SMP の SQL Server の構成のベスト プラクティス  
リモート テーブル コピーを受信する SMP の SQL Server を構成する場合は、パフォーマンスを向上させるために次のベスト プラクティスを使用します。  
  
1.  SQL Server 製品ドキュメントに記載されているベスト プラクティスに従います。 たとえば、データの暗号化を有効にします。 SQL Server の保護の詳細については、次を参照してください。 [SQL Server のセキュリティで保護する](../relational-databases/security/securing-sql-server.md)msdn です。  
  
2.  一括ログまたは単純復旧モデルを使用します。  
  
    エクスポート操作の並列のデータの中に、データを一括を新しく作成した変換先テーブルに挿入します。 一括挿入中にパフォーマンスを高めるためには、一括ログ記録を使用する転送先データベースまたは単純復旧モデルを設定します。  
  
3.  Batch_size オプションを使用すると、ログ領域を再利用できます。  
  
    一括ログまたは単純復旧モデルの使用、一括挿入データのログ記録を最小限に抑えるがいくつかのログ記録が引き続き発生します。 ログ ファイルが大きくなりすぎたことを防ぐためには、定期的にログ領域を解放するのに SQL Server の batch_size オプションを使用します。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
