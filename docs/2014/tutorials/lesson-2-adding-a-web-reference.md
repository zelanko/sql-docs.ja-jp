---
title: 'レッスン 2: Web 参照の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dd4b9edc8c054a7fa2ec84bdc8d892e5b5a903a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63316007"
---
# <a name="lesson-2-adding-a-web-reference"></a>レッスン 2 : Web 参照の追加
  Web サービスの探索とは、クライアントが Web サービスを検索し、そのサービス記述を取得する処理です。 
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の Web サービス探索処理では、事前に定義されたアルゴリズムに従って、Web サイトの問い合わせが行われます。 この処理の目的はサービス記述を見つけることです。サービス記述とは、WSDL (Web サービス記述言語) を使用する XML ドキュメントです。  
  
 サービス記述には、利用可能なサービスとこれらのサービスとの対話方法が記述されています。 サービス記述がない場合は、プログラムから Web サービスと対話することはできません。  
  
 アプリケーションには、Web サービスと通信する方法とランタイムで Web サービスを検出する方法を実装する必要があります。 これを実現するには、プロジェクトに Web サービス用の Web 参照を追加します。その結果、プロキシ クラスが生成されます。プロキシ クラスは、Web サービスとのインターフェイスとなり、Web サービスのローカル表記を提供します。 詳細については、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ドキュメントの「方法 : XML Web サービス プロキシを生成する」を参照してください。  
  
### <a name="to-add-a-web-reference"></a>Web 参照を追加するには  
  
1.  [**プロジェクト**] メニューの [**サービス参照の追加**] をクリックします。  
  
2.  [**サービス参照の追加**] ダイアログボックスで、[**詳細設定**] をクリックします。  
  
3.  [**サービス参照の設定**] ダイアログボックスで、[ **Web 参照の追加**] をクリックします。  
  
4.  [ **Web 参照の追加**] ダイアログボックスの [ **url** ] ボックスに、レポートサーバー Web サービスのサービスの説明を取得するための url http://localhost/reportserver/reportservice2010.asmxを入力します (など)。 次に、[実行] ボタンをクリックし**て、Web**サービスに関する情報を取得します。  
  
     \- - または -  
  
     レポートサーバー Web サービスがローカルコンピューターに存在する場合は、ブラウザーペインの [**ローカルコンピューター] リンクで web サービス**をクリックします。 次に、表示された一覧から ReportService2010 Web サービスのリンクをクリックします。  
  
5.  [ **Web 参照名**] ボックスで、web 参照の名前を ReportService2010 に変更します。これは、この web 参照に使用する名前空間です。  
  
6.  [**参照の追加**] をクリックして、ターゲット web サービスの web 参照を追加します。  
  
     
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] により、サービス記述がダウンロードされ、アプリケーションとレポート サーバー Web サービス間のインターフェイスとなるプロキシ クラスが生成されます。 また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。  
  
7.  [プロジェクト] メニューの **[参照の追加]** をクリックします。  
  
8.  [**参照の追加**] ダイアログボックスの [ **.net** ] タブで、[ **system.web. Services**] を選択し、[ **OK**] をクリックします。  
  
 詳細については、「[SOAP API へのアクセス](../reporting-services/report-server-web-service/accessing-the-soap-api.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Web サービス](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レッスン 3: Web サービスへのアクセス](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Visual Basic または Visual C&#35; &#40;SSRS チュートリアルを使用したレポートサーバー Web サービスへのアクセス&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
