---
title: 高可用性のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2d98e061fc71bfa5b9e5b076004934e74cabd35c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112732"
---
# <a name="high-availability-support"></a>高可用性のサポート
  CDC Service for Oracle は高可用性向けに設計されています。 次の機能は、高可用性のサポートの一部を形成します。  
  
-   CDC Service for Oracle はファイル リソース (ローカルまたはそれ以外) を使用しません。 CDC Service for Oracle のすべての状態は、対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに格納されます。 これにより、サービスが実行されているコンピューターに障害が発生した場合、同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用する別のコンピューターでサービスを簡単に開始できます。 復旧時間を軽減するために、長い Oracle トランザクションまたは実行時間のかかる Oracle トランザクションは対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のステージング テーブルに保持されます。これにより、障害 (またはサービスの再起動) 後に多数の Oracle トランザクション ログを再度スキャンする必要がなくなります。  
  
-   CDC Service for Oracle では、クラスター化された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用できます。そのため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが別のクラスター ノードにフェールオーバーした後の復元が可能です。 Oracle CDC Service のコンピューターの管理者は、Oracle CDC サービスを作成するときに、クラスター化された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続情報のみを指定する必要があります。  
  
-   CDC Service for Oracle を使用できる、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **AlwaysOn**データベース ミラーリング機能。 このサポートを利用するには、MSXDBCDC データベースとすべての CDC データベースが同じ可用性グループ内に存在している必要があります。 また、適切なを指定する Oracle CDC Service のコンピューターの管理者が必要に**AlwaysOn**への接続情報、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可用性グループ (接続のプロパティなど、 `Failover_Partner and Network=dbmssocn`)。 これにより、フェールオーバー後のデータベースのセカンダリ レプリケーションで CDC サービスが処理を自動的に再開することが可能になります。  
  
-   CDC Service for Oracle は、( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共に、または独立して) Windows フェールオーバー クラスター上の汎用サービス リソースとして構成し、クラスターでの CDC 処理のフェールオーバーとフォールバックを簡素化することができます。 CDC Service for Oracle をフェールオーバー クラスターのリソースとして構成するには、システム管理者が CDC Service for Oracle をフェールオーバー クラスターの各ノードで汎用サービス リソースとして設定する必要があります。  
  
-   CDC Service for Oracle は Oracle RAC をサポートします。これにより、いずれかの Oracle RAC ノードがダウンしている場合でも、Oracle データベースと通信し、ログを処理できます。  
  
  
