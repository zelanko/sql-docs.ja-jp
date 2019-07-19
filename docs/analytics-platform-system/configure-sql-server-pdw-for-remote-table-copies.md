---
title: リモート テーブル コピー用の並列データ ウェアハウスの構成 |Microsoft Docs
description: リモート テーブル コピー機能を使用して非アプライアンス サーバー上の SMP SQL Server データベースにテーブルをコピーする並列データ ウェアハウスを構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4f3abd60cb4f87abc5e6cbdc420fc6c551b0ab15
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961223"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>リモート テーブル コピー用の並列データ ウェアハウスを構成します。
リモート テーブル コピー機能を使用して非アプライアンス サーバー上の SMP SQL Server データベースにテーブルをコピーする SQL Server PDW を構成する方法について説明します。  
  
このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください。[リモート テーブル コピー](remote-table-copy.md)します。  
  
## <a name="before-you-begin"></a>はじめに  
リモート テーブル コピーを使用する SQL Server PDW を構成するには次の操作を行う必要があります。  
  
-   Analytics Platform System 管理者アカウントに直接ログインすることができます、  <strong>*appliance_domain*-AD01</strong>と <strong>*appliance_domain*-AD02</strong>ノード。  
  
-   ホスト名または移行先サーバーの IP 名を知っています。  
  
## <a name="HowToPDW"></a>SQL Server PDW は、リモート テーブルのコピーを構成します。DNS のホスト名を更新します。  
**CREATE REMOTE TABLE**ステートメント、リモート テーブルのコピーに使用される IP アドレスまたは SMP Windows システムの IP 名を使用して、移行先サーバーを指定します。 IP 名を使用するには、DNS サーバーに正常な名前解決のためのエントリを追加する必要があります。  
  
次の手順では、DNS サーバーを更新する方法を説明します。  
  
1.  アクティブな AD ノードにログオン (通常 <strong>*appliance_domain*-AD01</strong>)。  
  
2.  DNS マネージャーを開きます。 下にあるこの**管理ツール**で、**開始**メニュー。  
  
3.  IP 名を追加するのにには、DNS マネージャーを使用します。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[DNS フォワーダーを使用して非アプライアンス DNS 名を解決するには](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
