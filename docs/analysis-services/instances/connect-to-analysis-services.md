---
title: "Analysis Services に接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances of Analysis Services, connections
ms.assetid: 73ee8171-3379-4384-bfc8-071b3eebbc8f
caps.latest.revision: 46
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7b0e2b4020f3f9d27be84c1a6dc2f0944da88f5f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="connect-to-analysis-services"></a>Analysis Services への接続
  このセクションでは、接続文字列のプロパティ、接続に使用するクライアント ライブラリ、Analysis Services がサポートする認証方法、および接続の設定方法やサーバーをオフラインにする前の接続解除方法について説明します。  
  
## <a name="analysis-services-connections"></a>Analysis Services の接続  
 Analysis Services では、ネットワーク プロトコルとして TCP を使用し、通信プロトコルとして XML for Analysis (XMLA) を使用します。 最下位レベルでは、Analysis Services で提供されるすべてのクライアント ライブラリが TCP 経由の XMLA を実装します。 未加工の XMLA に基づいてアプリケーションをビルドすることができますが、ほとんどのアプリケーションおよびアプリケーション開発者は、クライアント ライブラリを使用することで、クライアント ライブラリが提供するオブジェクト モデルとコーディングの効率性を活用できます。 Analysis Services へのクライアント接続では、スタック全体に TCP を使用できない場合に IIS を接続の仲介役として使用することができます。 IIS を介して HTTP アクセスを使用する利点の 1 つに、接続文字列で資格情報を渡すアプリケーションから接続できるという点があります。  
  
 接続に関するすべての説明には、通常は認証が含まれます。 SQL Server のその他の機能とは異なり、Analysis Services は Windows の資格情報だけを使用します。 SQL Server データベース認証、要求認証、フォーム ベースの認証、または Analysis Services へのバックエンド接続でのダイジェストは使用できません。 このセクションでは、認証の詳細について説明します。  
  
##  <a name="bkmk_clientApps"></a> 接続タスク  
  
|リンク|タスクの説明|  
|----------|----------------------|  
|[クライアント アプリケーションからの接続 (Analysis Services)](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)|Analysis Services を初めて使用する場合は、このトピックを参照して、Analysis Services で最も頻繁に使用されるツールとアプリケーションについて確認します。|  
|[接続文字列プロパティ (Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md)|Analysis Services には多くのサーバー プロパティやデータベース プロパティがあるので、インスタンスやデータベースの構成方法に関係なく、特定のアプリケーションの接続をカスタマイズすることができます。|  
|[Analysis Services でサポートされる認証方法](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)|このトピックでは、Analysis Services で使用する認証方法について簡単に説明します。|  
|[Kerberos の制約付き委任のための Analysis Services の構成](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md)|多くのビジネス インテリジェンス ソリューションでは、許可されたデータだけが各ユーザーに返されるようにするための権限借用が必要です。 このトピックでは、権限借用を使用するための要件について説明します。 また、Kerberos 制約付き委任に対応するように Analysis Services を構成するための手順についても説明します。|  
|[Analysis Services インスタンスの SPN 登録](../../analysis-services/instances/spn-registration-for-an-analysis-services-instance.md)|Kerberos 認証には、マルチサーバー ソリューションでユーザー ID を借用または委任するサービスに有効なサービス プリンシパル名 (SPN) が必要です。 このトピックの情報を使用して、Analysis Services 用の SPN 登録の構成と手順を学習します。|  
|[インターネット インフォメーション サービス (IIS) 8.0 上の Analysis Services への HTTP アクセスの構成](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|基本認証またはクロスドメインの境界は、HTTP アクセス用に Analysis Services を構成する 2 つの重要な理由です。|  
|[Analysis Services 接続に使用するデータ プロバイダー](../../analysis-services/instances/data-providers-used-for-analysis-services-connections.md)|Analysis Services には、サーバー操作または Analysis Services データにアクセスするためのクライアント ライブラリが 3 つ用意されています。 このトピックでは、ADOMD.NET、Analysis Services 管理オブジェクト (AMO)、および Analysis Services OLE DB プロバイダー (MSOLAP) について簡単に説明します。|  
|[Analysis Services サーバー上のユーザーとセッションの切断](../../analysis-services/instances/disconnect-users-and-sessions-on-analysis-services-server.md)|サーバーをオフラインにする前やベースライン パフォーマンス テストを行う前には、既存の接続とセッションをクリアします。|  
  
## <a name="see-also"></a>参照  
 [インストール後の構成 (Analysis Services)](../../analysis-services/instances/post-install-configuration-analysis-services.md)   
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
  
  

