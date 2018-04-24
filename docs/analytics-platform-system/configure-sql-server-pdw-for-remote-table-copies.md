---
title: リモート テーブルのコピーの並列データ ウェアハウスの構成 |Microsoft ドキュメント
description: 非アプライアンス サーバー上の SMP SQL Server データベースにテーブルをコピーするリモート テーブルのコピー機能を使用する並列データ ウェアハウスを構成する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3f71a0c67639918820bca8f6f8f38b9f354154f3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>リモート テーブルのコピーの並列データ ウェアハウスを構成します。
SQL Server PDW アプライアンス以外のサーバー上の SMP SQL Server データベースにテーブルをコピーするリモート テーブルのコピー機能を使用するを構成する方法について説明します。  
  
このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください。[リモート テーブルのコピー](remote-table-copy.md)です。  
  
## <a name="before-you-begin"></a>はじめに  
リモート テーブルのコピーを使用する SQL Server PDW を構成するのには、次の操作を行います。  
  
-   直接ログオンする権限を持つ分析プラットフォーム システム管理者アカウントがある、***appliance_domain *-AD01**と ***appliance_domain *-AD02**ノード。  
  
-   ホスト名または移行先サーバーの IP 名を知っています。  
  
## <a name="HowToPDW"></a>リモート テーブルのコピーの SQL Server PDW の構成: DNS のホスト名を更新  
**CREATE REMOTE TABLE**リモート テーブルのコピーを使用するステートメントは、IP アドレスまたは SMP Windows システムの IP 名を使用して、移行先サーバーを指定します。 IP 名を使用するのには、DNS サーバーに名前解決の成功のエントリを追加する必要があります。  
  
次の手順では、DNS サーバーを更新する方法を説明します。  
  
1.  作業中の AD ノードにログオン (通常 ***appliance_domain *-AD01**)。  
  
2.  DNS マネージャーを開きます。 これは、下にある **管理ツール**で、**開始**メニュー。  
  
3.  IP 名を追加するのにには、DNS マネージャーを使用します。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[非アプライアンスの DNS 名を解決するのには、DNS フォワーダーを使用します。](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
