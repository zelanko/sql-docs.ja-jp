---
title: OLAP エンジン サーバー コンポーネント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 535d1e05fc82882e0a2b5ea43ac9b2147e62338b
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388015"
---
# <a name="olap-engine-server-components"></a>OLAP エンジンのサーバー コンポーネント
  のサーバー コンポーネント[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]は、Windows サービスとして実行される**msmdsrv.exe**アプリケーションです。 このアプリケーションは、セキュリティ コンポーネント、XML for Analysis (XMLA) リスナー コンポーネント、クエリ プロセッサ コンポーネント、および次の機能を実行するその他多くの内部コンポーネントで構成されています。

-   クライアントから受信したステートメントの解析

-   メタデータの管理

-   トランザクションの処理

-   計算の処理

-   ディメンションおよびセル データの格納

-   集計の作成

-   クエリのスケジュール設定

-   オブジェクトのキャッシュ

-   サーバー リソースの管理

## <a name="architectural-diagram"></a>アーキテクチャの図
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスはスタンドアロン サービスとして実行され、サービスとの通信は、HTTP または TCP を使用して XML for Analysis (XMLA) 経由で行われます。 AMO は、ユーザー アプリケーションと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスの間のレイヤーです。 このレイヤーは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理オブジェクトへのアクセスを提供します。 AMO は、クライアント アプリケーションからコマンドを受け取り、それを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス用の XMLA メッセージに変換するクラス ライブラリです。 AMO は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス オブジェクトをクラスとして、エンド ユーザー アプリケーションに提示します。このクラスには、コマンドを実行するメソッド メンバーと、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトのデータを持つプロパティ メンバーが含まれます。

 次の図は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] コンポーネントのアーキテクチャを示しており、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス内で実行されるすべての主要な要素と、インスタンスと連携するすべてのユーザー コンポーネントを含んでいます。 また、この図は、XML for Analysis (XMLA) リスナーと、HTTP または TCP のいずれかを使用する以外に、インスタンスにアクセスする方法がないことも示しています。

 ![Analysis Services のシステム アーキテクチャ図](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services のシステム アーキテクチャ図")

## <a name="xmla-listener"></a>XMLA リスナー
 XMLA リスナー コンポーネントでは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] とそのクライアントの間のすべての XMLA 通信が処理されます。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini ファイルの構成設定を使用して、インスタンスがリッスンするポートを[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]指定できます。 このファイルの 0 の値は、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が既定のポートをリッスンすることを示します。 特に指定がなければ、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では次の既定の TCP ポートが使用されます。

|Port|説明|
|----------|-----------------|
|2383|の既定の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスです。|
|2382|の他のインスタンスの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]リダイレクタ|
|サーバーの起動時に動的に割り当てられます。|の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]名前付きインスタンスです。|

 詳細については[、「分析サービスへのアクセスを許可するように Windows ファイアウォールを構成](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)する」を参照してください。

## <a name="see-also"></a>参照
 [オブジェクト名前付けルール&#40;物理](object-naming-rules-analysis-services.md)[アーキテクチャ&#40;分析サービス&#41;- 多次元データ&#41;](understanding-microsoft-olap-physical-architecture.md)[論理アーキテクチャ&#40;分析サービス - 多次元データ&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)


