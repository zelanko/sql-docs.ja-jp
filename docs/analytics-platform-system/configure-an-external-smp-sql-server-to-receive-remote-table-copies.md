---
title: リモート テーブルのコピー - Parallel Data Warehouse を受信する SQL Server の構成 |Microsoft ドキュメント
description: 並列データ ウェアハウスからリモート テーブルのコピーを受信する外部 SMP SQL Server インスタンスを構成する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ae6799d468d57dec04046b443c613823c0a8cb8c
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies---parallel-data-warehouse"></a>外部の SMP SQL Server を受け取りますが、リモート テーブルの並列データ ウェアハウスを構成します。
並列データ ウェアハウスからリモート テーブルのコピーを受信する外部の SQL Server インスタンスを構成する方法について説明します。  

このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください。[リモート テーブルのコピー](remote-table-copy.md)です。  
  
## <a name="before-you-begin"></a>はじめに  
外部の SQL Server を構成することができます、前に次の操作を行う必要があります。  
  
-   ある Windows システムで SQL Server 2008 Enterprise Edition、またはそれ以降のバージョンをインストールまたは既にインストールされている準備ができています。 説明に従って、Windows システムが構成されている必要があります[構成、外部 Windows システムに表示されるリモート テーブルのコピーを使用して InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)です。  
  
-   SQL Server インスタンスと、Windows システムを構成する機能を持つ Windows 管理者アカウントです。  
  
-   SQL Server ログイン アカウント (SQL Server が既にインストールされている) 場合ログインを作成し、移行先のデータベースに対する権限を許可する機能を使用します。  
  
## <a name="HowToSQLServer"></a>リモート テーブルのコピーを受信する外部の SMP SQL サーバーを構成します。  
リモート テーブルのコピー機能では、Windows システムで実行されている外部 SMP SQL Server データベースに SQL Server PDW アプライアンスからテーブルをコピーします。 リモート テーブルのコピーを受信する外部の Windows システムを構成した後は、次の手順は、インストールして、Windows システム上に SQL Server を構成するのには。  
  
SQL Server を構成するのには、次の手順を使用します。  
  
1.  Windows システムでは、SQL Server 2008 Enterprise Edition またはそれ以降のバージョンをインストールします。 これは、SMP SQL Server と呼ばれます。  
  
2.  固定の TCP ポートで TCP/IP 接続を受け入れるように SQL Server を構成します。 この構成は、既定では無効し、SQL Server PDW SMP SQL Server への接続に使用できるように有効にする必要があります。  
  
3.  Windows ファイアウォールを無効にするか、Windows ファイアウォールが有効では動作できるように、SMP SQL Server の TCP ポートを構成します。  
  
4.  SQL Server 認証モードを許可する SQL Server を構成します。 並列データを SQL Server のアカウントを使用して認証を常にエクスポートします。  
  
5.  認証に使用される SMP SQL サーバー上の SQL Server アカウントを決定します。 そのアカウントの作成、削除、および並列のデータのエクスポート操作の転送先データベース内のテーブルにデータを挿入するための権限を付与します。  
  
## <a name="BPSQLConfig"></a>リモート テーブルのコピーの SMP SQL Server の構成のベスト プラクティス  
リモート テーブルのコピーを受け取る SMP SQL Server を構成する場合は、パフォーマンスを向上させるために、次のベスト プラクティスを使用します。  
  
1.  SQL Server の製品マニュアルに記載されたベスト プラクティスに従います。 たとえば、データの暗号化を有効にします。 SQL Server の保護の詳細については、次を参照してください。 [SQL Server のセキュリティで保護する](../relational-databases/security/securing-sql-server.md)msdn です。  
  
2.  一括ログまたは単純復旧モデルを使用します。  
  
    エクスポート操作の並列のデータの中に、データを一括新しく作成されたコピー先のテーブルに挿入します。 一括挿入中にパフォーマンスを高めるためには、一括ログ記録を使用する移行先のデータベースまたは単純復旧モデルを設定します。  
  
3.  Batch_size オプションを使用すると、ログ領域を再利用できます。  
  
    ただし、一括ログまたは単純復旧モデルの最小一括挿入データのログ記録を使用して、いくつかのログ記録が引き続き発生します。 ログ ファイルが大きくなりすぎることを防ぐためには、定期的にログ領域を解放するのに SQL Server batch_size オプションを使用します。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
