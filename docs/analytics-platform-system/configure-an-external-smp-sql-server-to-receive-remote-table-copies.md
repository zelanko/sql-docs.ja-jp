---
title: リモート テーブルのコピー (PDW) を受信する外部の SMP SQL Server を構成します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bbd2ed6-064e-4b45-b67b-608dc0f2b2bc
caps.latest.revision: 13
ms.openlocfilehash: 94b62dbae331c19fa97c1625a53804f4cd96bfa5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies"></a>リモート テーブルのコピーを受け取る外部 SMP SQL サーバーを構成します。
SQL Server PDW からリモート テーブルのコピーを受信する外部の SQL Server インスタンスを構成する方法について説明します。  
  
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
  
