---
title: "クライアント アーキテクチャの要件の Analysis Services の開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- local mining models [Analysis Services]
- Analysis Services, architecture
- providers [Analysis Services]
- data pumps [Analysis Services]
- client architecture [Analysis Services]
- local cubes [Analysis Services]
ms.assetid: 03a8eb6b-159f-4a0a-afbe-06a2424b6090
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5fa4192b9852d88100c1520a8c274dac199e1f48
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="client-architecture-requirements-for-analysis-services-development"></a>Analysis Services 開発に関するクライアント アーキテクチャの要件
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] シン クライアント アーキテクチャをサポートしています。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]計算エンジンは完全サーバーに基づくため、サーバー上のすべてのクエリで解決されます。 つまり、クエリごとにクライアントとサーバー間での単一ラウンド トリップが必要です。この結果、クエリの複雑さが増すにつれてパフォーマンスが変化します。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のネイティブ プロトコルは、XML for Analysis (XMLA) です。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、クライアント アプリケーション用のデータ アクセス インターフェイスがいくつか用意されていますが、これらのすべてのコンポーネントは XML for Analysis を使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のインスタンスと通信を行います。  
  
 異なるプログラミング言語をサポートするため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ではいくつかの異なるプロバイダーが用意されています。 プロバイダーは、インターネット インフォメーション サービス (IIS) を通じて TCP/IP または HTTP で SOAP パケットの XML for Analysis を送受信することによって [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーと通信します。 IIS によってインスタンス化された、データ ポンプと呼ばれる COM オブジェクトを使用する HTTP 接続は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データのパイプとして機能します。 データ ポンプでは、HTTP ストリーム内に含まれる、基になるデータはまったく検証されません。また、基になるデータ構造はデータ ライブラリ内にあるコードではまったく使用できません。  
  
 ![Analysis Services の論理クライアント アーキテクチャ](../../../analysis-services/multidimensional-models/olap-physical/media/as-clientarch9.gif "Analysis Services の論理クライアント アーキテクチャ")  
  
 Win32 クライアント アプリケーションから [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーへの接続には、OLE DB for OLAP インターフェイスまたは Microsoft Visual Basic® などのコンポーネント オブジェクト モデル (COM) オートメーション言語用の Microsoft® ActiveX® データ オブジェクト (ADO) オブジェクト モデルを使用できます。 .NET 言語で記述されたアプリケーションでは、ADOMD.NET を使用して [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーに接続できます。  
  
 既存のアプリケーションは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] プロバイダーのいずれかを使用するだけで、変更しなくても [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] と通信できます。  
  
|プログラミング言語|データ アクセス インターフェイス|  
|--------------------------|---------------------------|  
|C++|OLE DB for OLAP (OLE DB for OLAP)|  
|Visual Basic 6|ADO MD (ADO MD)|  
|.NET 言語|ADO MD.NET|  
|SOAP をサポートするすべての言語|XML for Analysis (XML for Analysis)|  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 大小両方の組織で展開を完全にスケーラブルな中間層で Web アーキテクチャがあります。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] には、Web サービスへの広範な中間層のサポートが用意されています。 ASP アプリケーションはサポートされて OLE DB で OLAP および ADO MD、ASP.NET アプリケーションは ADOMD.NET によってサポートされています。 次の図のように、中間層は、多数の同時ユーザーに対応できるスケーラブルな層です。  
  
 ![中間層アーキテクチャの論理図](../../../analysis-services/multidimensional-models/olap-physical/media/as-midtierarch9.gif "中間層アーキテクチャの論理図")  
  
 クライアントおよび中間層アプリケーションは、いずれも、プロバイダーを使用せずに直接 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] と通信できます。 クライアントおよび中間層アプリケーションによっては、TCP/IP、HTTP、または HTTPS を使用して SOAP パケットで XML for Analysis を送信する場合もあります。 また、クライアントは SOAP をサポートする任意の言語を使用して記述されている場合もあります。 この場合、通信の管理には、TCP/IP を使用したサーバーへの直接接続が記述されている場合でも、HTTP を介したインターネット インフォメーション サービス (IIS) を使用する方法が最も管理が簡単です。 これが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] に最適のシン クライアント ソリューションです。  
  
## <a name="analysis-services-in-tabular-or-sharepoint-mode"></a>テーブル モードまたは SharePoint モードの Analysis Services  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、表形式データベースと、xVelocity メモリ内分析エンジン (VertiPaq) モードで、サーバーを起動する[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]SharePoint サイトにパブリッシュされたブック。  
  
 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] および[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]作成と SharePoint モードまたは表形式モードをそれぞれを使用するインメモリ データベースのクエリがサポートされている唯一のクライアント環境です。 埋め込まれた[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]、Excel を使用して作成したデータベースおよび[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]ツールは、Excel ブック内に含まれ、Excel .xlsx ファイルの一部として保存されます。  
  
 ただし、キューブ データをブックにインポートすると、従来のキューブに格納されたデータを [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックで使用できます。 また、SharePoint サイトにパブリッシュされている場合、別の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックからデータをインポートすることもできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックのデータ ソースとしてキューブを使用する場合、キューブから取得するデータは、MDX クエリとして定義されます。ただし、データはフラット化スナップショットとしてインポートされます。 キューブのデータは、対話的に操作したり、更新したりすることはできません。  
  
 データ ソースとしての SSAS キューブの使用の詳細については、次を参照してください。、 [Power Pivot for Excel](http://go.microsoft.com/fwlink/?LinkId=164234)です。  
  
### <a name="interfaces-for-power-pivot-client"></a>Power Pivot クライアント用のインターフェイス  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Analysis Services の確立されたインターフェイスおよび言語を使用して、ブック内で xVelocity メモリ内分析エンジン (VertiPaq) ストレージ エンジンと対話します。 AMO と ADOMD.NET、および MDX と XMLA です。 アドイン内では、メジャーは、Excel、Data Analysis Expressions (DAX) と同様の数式言語を使用して定義されます。 DAX の式は、インプロセス サーバーに送信される XMLA メッセージ内に埋め込まれます。  
  
### <a name="providers"></a>[プロバイダー]  
 間の通信[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]Excel MSOLAP OLEDB プロバイダー (バージョン 11.0) を使用するとします。 MSOLAP プロバイダー内には、4 つの異なるモジュールまたはトランスポートがあり、クライアントとサーバー間のメッセージの送信に使用できます。  
  
 **TCP/IP**の通常のクライアント サーバー接続に使用します。  
  
 **HTTP**または SharePoint への呼び出しによって、SSAS データ ポンプ サービスを使用して HTTP 接続に使用する[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]Web サービス (WS) コンポーネントです。  
  
 **INPROC**インプロセス エンジンへの接続を使用します。  
  
 **チャネル**との通信用に予約されて、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint ファーム内のシステム サービスです。  
  
## <a name="see-also"></a>参照  
 [OLAP エンジンのサーバー コンポーネント](../../../analysis-services/multidimensional-models/olap-physical/olap-engine-server-components.md)  
  
  
