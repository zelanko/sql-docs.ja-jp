---
title: XMLA の概念 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 429d1bc09714d15cfb8fbd851c72e01dd8ba198b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="xmla-concepts"></a>XMLA の概念
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  XML for Analysis (XMLA) オープン スタンダードでは、World Wide Web 上に存在するデータ ソースへのアクセスがサポートされています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] XMLA 1.1 仕様あたり XMLA を実装します。  
  
 XML for Analysis (XMLA) は Simple Object Access Protocol (SOAP) ベースの XML プロトコルで、Web 上に存在するあらゆる標準的な多次元データ ソースへの汎用データ アクセスを提供することを目的に特別に設計されています。 XMLA がコンポーネント オブジェクト モデル (COM) を公開するクライアント コンポーネントを配置する必要もなくなりますまたは[!INCLUDE[msCoName](../../../includes/msconame-md.md)].net&#xa0;framework インターフェイスです。 インターネット環境では、サーバーとのやり取りに多くの時間とリソースが費やされ、データへの状態を保持する接続によってサーバーへのユーザー接続が制限されることがありますが、XMLA はそのようなインターネット環境のために最適化されています。  
  
 XMLA は、ネイティブ プロトコルは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のクライアント アプリケーションとのインスタンスの間のすべての対話に使用[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 を完全にサポートし、さらには、メタデータ管理、セッション管理、およびロック機能をサポートする拡張機能を提供します。 分析管理オブジェクト (AMO) と ADOMD.NET はいずれも、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとの通信に XMLA プロトコルを使用します。  
  
## <a name="handling-xmla-communications"></a>XMLA 通信の処理  
 XMLA オープン スタンダードに 2 つの一般的にアクセス可能なメソッドがについて説明します。 **Discover**と**Execute**です。 これらのメソッドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上で送受信される情報を処理するために、XML がサポートする疎結合のクライアント/サーバー アーキテクチャを使用します。  
  
 **Discover**メソッドは、Web サービスから情報およびメタデータを取得します。 この情報には、使用可能なデータ ソースの一覧、任意のデータ ソース プロバイダーに関する情報などが含まれます。 データ ソースから取得されるデータは、プロパティによって定義および成形されます。 **Discover**メソッドはさまざまな種類のクライアント アプリケーションがありますのデータ ソースからの情報を定義するための一般的な方法では[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 プロパティと汎用インターフェイスを使用すれば、クライアント アプリケーション内の既存の機能を書き直さなくても拡張機能を利用できます。  
  
 **Execute**メソッドにより、アプリケーションを XMLA データ ソースに対してプロバイダー固有のコマンドを実行します。  
  
 XMLA プロトコルは Web アプリケーション用に最適化されていますが、LAN 指向のアプリケーションでもこれを利用できます。 次のようなアプリケーションは、この XML ベースの API の利点を活用できます。  
  
-   クライアント/サーバー間の柔軟な通信テクノロジを必要とするクライアント/サーバー アプリケーション  
  
-   複数のオペレーティング システムを扱うことを想定したクライアント/サーバー アプリケーション  
  
-   サーバー容量を増やすために大きなステートを要求しないクライアント  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA と統合ディメンショナル モデル  
 XMLA は、統合ディメンショナル モデル (UDM) の手法を採用しているビジネス インテリジェンス アプリケーションによって使用されるプロトコルです。  
  
  
